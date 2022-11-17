---
title: "Cybersecurity Homelab for Dectection and Monitoring"
date: 2022-10-07T14:21:08-05:00
draft: false
tags: ["Self-Hosted", "hardware", "tech", "DNS", "opendns", "Pfsense", "HACK"]
---

# Cybersecurity homelab for dectection & monitoring


# Building a cybersecurity homelab for detection & monitoring

This homelab will help you apply concepets used in real-world large-scale/enterprise infrastructe

## What is a homelab

A homelab is a place where you can safely do experiments without messing anything up

## Content

*   installing VMware Workstation as hypervisor
*   Configuring Pfsense firewall for network segmentation & security
*   Configuring Security Onion as an all-in-one IDS, Security, and Log Management solution
*   Configuring Kali Linux as an attack machine
*   Configuring Windows Server 2019 as a DC
*   Configuring Windows server
*   Configuring Splunk

![network topology](/topology.png)

## Downloading & installing vmware workstation pro

[VMware workstation pro](https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html)

## Configuring Pfsense

Pfsense will be configured as a firewall to segment our private homelab network and will be only accessible from our Kali Linux VM

Click "Create a new Virtual Machine" on VMware Workstation homescreen

Make sure "Typical (recommenced)" is selected and click Next.

![network topology](/start.png)

Click browser and navigate to the folder where your Pfsense file is located.

Click Next.

![iso](/os.png)

Rename your Virtual Machine. Preferably "pf-l1"

Click next

20GB disk size is sufficient for this VM

Ensure that the "Split virtual disk into multiple files" option is selected

Click next.

![disk](/disk.png)

Click "Customize Hardware".

Increase the memory to 2GB

Add 5 network adapters and correspond them with VMnet interface as shown below. Then click finsh

![network](/network.png)

The Pfsense machine will power on and start with this screen. Accept all the defaults.Pfsense will configure and reboot. ![Pfsense](/Pfsense.png)

Ones you are in the home screen of Pfsense we will get start setting up network adapters.

Enter option 1

**Should VLANS be set up now \[y:n\]?:**n

Enter **em0, em1, em2, em3, em4 & em5** respectively for each consecutive question

**Do you want to proceed \[y:n\]?:**y

![em](/em.png) ![em2](/em2.png)

Enter option 2 We'll start with the LAN interface (2) The IP address **192.168.1.1** is going to be used to access the Pfsense WebGUI via the Kali Machine use the configuration below for the LAN interface.

![opt1](/opt1.png)

Use the configuration below for the OPT1 interface.

![opt1-1](/opt1-1.png)

Use the configuration below for the OPT2 interface

![opt2](/opt2.png)

Leave the OPT3 interface without an IP as it is going to have the span port with traffic that Security Onion will be monitoring. Use the configuration for the OPT4 interface.

![opt4](/opt4.png)

## Configuring Security Onion

This will be the all-in-one IDS,Security Monitoring, and Log Management solution [Download the Security Onion ISO file from here](https://github.com/Security-Onion-Solutions/securityonion/blob/master/VERIFY_ISO.md)

Select Typical installation and click next.

Installer disc image file, SO ISO file path and Click Next.

On the next screen chose Linux, CentOS 7 64-Bit and click Next.

Name the VM l1-sec and click next.

Minimum 200GB but if you can use 400GB

Then click "Customize Hardware" and do the following

~Change memory to 4-32GB

~ Add two Network Adapters and assign them Vmnet4 & Vmnet5 respectively.

![sec](/sec.png)

Power on the virtual machine and click enter when prompted

After the initial stages of loading, type "yes" when prompted

![sec1](/sec1.png)

Set a username & password

After Security Onion reboots, we will finish up the install.

Enter the Username & password.

Select "Yes"

![sec2.png](/sec2.png)

Select the EVAL option

![sec3.png](/sec3.png)

Type "AGREE"

![sec4](/sec4.png)

Select "Standard" ![sec5](/sec5.png)

Set a homename

Click the space bar to select ens33 as the management interface

![sec6](/sec6.png)

Set the addressing to DHCP.

![sec7](/sec7.png)

Select "YES" at the next prompt


Select "OK" at the next prompt.

Select "Direct" for the next prompt.

Select "ens35" as the monitor Interface.

![sec8](/sec8.png)

Select "Automatic" for the OS patch schedule.

Accept the default home network IP.

Accept all the defaults.

Enter an email address and password for the admin account.

Select "IP"

![sec9.png](/sec9.png)

Select "Yes" for the NTP server & accept the defaults

Take note of your final settings before proceeding! If possible take a screenshot

**Most important detail is the IP address for web access**

Select "YES"

### SecOnionMgmt/Analyst Machine

After installing Security Onion, having access to the web interface will be done from an external Ubuntu Desktop simulating a SOC/Security Analyst accessing a SIEM or any other tool from their device.

In order to this, you’ll first have to configure an Ubuntu Desktop. This is a very easy process and I’ll not be covering it in this write-up but it is covered in the video. Be sure to use all the default settings for the Ubuntu Desktop configuration.

[Download Ubuntu Desktop](https://ubuntu.com/download/desktop) [Install Ubuntu Desktop](https://getlabsdone.com/10-easy-steps-to-install-ubuntu-19-04-on-vmware-workstation-15/)

After this installation, run the ifconfig command on the Ubuntu Machine and take note of its IP Address.

Go back to your SO instance and run the following command


		sudo so-allow


Enter your password

Type a and wait for the process to complete

Type in the IP address of your Ubuntu desktop

Navigate to the SO IP on your ubuntu desktop

## Configuring Kali Linux

Kali Linux will be used as a attcker machine

[Download the Kali Linux ISO](https://www.offensive-security.com/kali-linux-vm-vmware-virtualbox-image-download/)

Before power on on the VM, change the Network Adapter to Vmnet2 and set the memory to 4GB, then power it on

Go throught the install

## Pfsense interfaces and Rules

We will use the Kali VM to setup Pfsense

Navigate to the web browser and search for 192.168.1.1

The default credence are "admin" & "Pfsense"

You'll be greeted with a "Wizard/Pfsense setup/" page.

Set the DNS server as 8.8.8.8 and 4.4.4.4

Then chose your timezone

At step **4 of 9**, untick the last two options.

at step **6 of 9**, set a new admin password.

### Set up Interface

Click on interface

Select LAN

For "Description", Change LAN to KALI as this is the Kali Interface

Scroll all the way down and Click Save

Then do this for the rest of the interfaces as show below

![Pfsense](/Pfsense.png)

For OPT3 be sure to Enable interface.

Back at Interfaces assignment select bridges

Click add

![Pfsense1](/Pfsense1.png)

Select **VictimNetwork** as the Member Interface

![Pfsense3](/Pfsense2.png)

Then select **Display Advanced**

Under **Advanced Configuration** for **Span Port**, select **"SPANPORT"**

Scroll all the way down and Click **Save**

![Pfsense3](/Pfsense3.png)

Click Firewall >> Rules

![Pfsense4](/Pfsense4.png)

Select the add button with arrow pointed downward

~Under "edit firewall rule" for Protocol select ANY

~ Scroll all the down and click save

This is most of what we need to do in Pfsense

### Configing Windows server as a domain controller

You can follow The Cyber Mentor guide to set up Active Directory and Windows 10 VM. We just need to set up the network stuff.

[The Cyber Mentor's youtube guide](https://www.youtube.com/watch?v=xftEuVQ7kY0) ![server1](/server1.png)

Navigate to **Control Panel > Network and Internet > Network Connections**

![server19](/server19.png)

### Windows 10 host networking

Naviage to Network Adapter settings

Right-click on Ethernet0 and select properties

Select IPv4 and set the ip address 192.168.2.21, use 192.168.2.1 as the default gateway, and use 192.168.2.10 as the DNS server.

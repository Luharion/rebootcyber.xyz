---
title: "Pihole"
date: 2022-10-07T14:06:43-05:00
draft: false
tags: ["DNS", "Self-Hosted"]
---



# PiHole


Pi-Hole is a Linux network-level advertisement and Internet tracker blocking application which acts as a DNS sinkhole and optionally a DHCP server, intended for use on a private network.
This allows you to block unwanted stuff and websites on your private network.DNS Sinkhole is a mechanism aimed at protecting users by intercepting DNS request attempting to connect to known malicious or unwanted domains and returning a false, or rather controlled IP address. The controlled IP address points to a sinkhole server defined by the DNS sinkhole administrator.

# How do you set up a Pi-Hole

First you will need a Linux box on a server or you can use Docker.Linux can be installed on an old laptop/desktop, or any raspberry pi. I will be using Ubuntu 20.04 LTS server to do this.

First you want to run `sudo apt update && sudo apt full-upgrade`

The creator of PiHole made a cool script to install automatically


`wget -O basic-install.sh https://install.pi-hole.net sudo bash basic-install.sh`

![Dns provider](/google.png)

You want to select Google DNS. For all other options just press enter


## User interface

You can go to your server IP in your web browser and the script will give you a password for the login. You can save this password somewhere or you can run

`pihole -a -p`

This will ask you to set a new password or not have a password. If you do not want anyone else on the pihole administrator page then set a strong password

![the dashboard of PiHole](/dash.png)

If you go to "Group Management" then "Adlists". You can set up websites you do not want people to go to on your network.Then go to Tools then Update Gravity to update the list.
There are adlist you can use get a lot of domains block or whitelisted depending on what you want to do with it. A poplar websites to go to is [PiHole adlist](https://firebog.net/) .
You can add this and it will block those domains. If you want to unblock a domains.

## How do I add this to my router

You need to log into your router. You router login will be different then everyone else. So look this up and normal the first link will tell you your default login. Then go to the DNS setting and change it to your server IP address. **So router will not allow you to change the DNS server settings.**
At that point you need to change then on every device you want to be connect to the PiHole.

If you want to get rid of just one domain then go to "Query Logs". Then if your IP address and find that request. Finally click the "Whitelist" button.


Now you do not have to see malicious links and ads. This can also be used to stop tracker and other stuff.

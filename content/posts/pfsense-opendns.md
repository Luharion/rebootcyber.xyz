---
title: "Pfsense Opendns"
date: 2022-10-07T14:13:22-05:00
draft: false
tags: ["opendns", "Pfsense", "DNS"]
---


# What is OpenDNS?

OpenDNS is a DNS sinkhole. This allows you to stop people from going to certain sites that you don't want them to go to. There is two version of OpenDNS called Umbrella this is the enterprise version and cost money. We will be using the consumer version called OpenDNS home.

First you need to set up an account. You will need an email address, password, and public IP. Ones you login in. You are ready to start

## How to set up OpenDNS?

First go to settings. Then type in your public IP. You can go to [What is my IP](https://whatismyipaddress.com/).

Then go to web content filtering. Set what you want to block. After this you can set up your DNS server in your router as

*   208.67.222.123
*   208.67.220.123

### How do I set this up for Pfsense

First login into your Pfsense router through the web portal.

Go to System/General Setup.

Then add a DNS server and use the 208 address above

Then save the changes.

Final we need to force ever network enable devices to use OpenDNS.

Go to Service/DHCP Server/ LAN

In the DNS setting type the above IP address and save

Final reboot your router

### How will this effect my network

This will force you not to go to sites than are part of the category that you set. If you do not want to effect you much then set to stop malware and stuff like that

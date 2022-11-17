---
title: "Dns"
date: 2022-10-30T09:23:20-05:00
draft: false
tags: [DNS, Study, Self-Hosted]
---

# What is DNS?
DNS is Domain Name Server, when you go to google.com, computers don't know what google.com is but it does know what an IP address is. So you have a file on you computer that says google.com equals 127.0.0.1. If you want to see the IP of google.com
```Shell
ping google.com
```
on any system.


# How does DNS work?
So when you go to a site like rebootcyber.xyz. First your pc check its DNS cache file then go to a local name server like your router or [pi-hole](/post/pihole.md). Then to a .com name server. Final to rebootcyber.xyz nameserver. If there are subdomains you want to go to then it will be the job of rebootcyber.xyz nameserver.


# Types of DNS

There are dns types. To begin A records are for IPv4 and AAAA records are for IPv6 address. Cnames are name alias of another server. MX records are for mail server. So like imap.gmail.com and smtp.gmail.com. NS are name for the domain this is normal handle by the company that you go your domain name from. PTR(Point Records) are reverse dns lookup. So if you look up 207.148.23.122 then it would tell you that is rebootcyber.xyz.


# Important note
I will be doing a tutorial on how to setup your own website, email server, search engine, and cloud server(maybe)

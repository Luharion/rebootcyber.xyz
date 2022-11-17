---
title: "Subdomain Takeover"
date: 2022-11-16T15:29:13-06:00
draft: false
---


# What are subdomains
To explain what a subdomain is you need to explain what a domain is. A domain name is the name of your website. So like
rebootcyber.xyz  or google.com is a domain. This allows users to just type in a name instead of a ip address. This makes it
so much easy to remeber a website.

Back to what a subdomain is. All a subdomain is a prefox added to a domain name to separte a section of a website. Site
owners primarily use subdomain to manage extensive section that require their own content. Subdomain function as a separte
website from its domain. This distinction enables developers to develop a section of a website without muddling a site's
overall intent.






# A subdomain takeover
If you have a subdomain on your website like searx.rebootcyber.xyz. If you  delete the config for searx.rebootcyber.xyz. You
might thing is fine but NO you are not. If this subdomain point to 3rd party sites like github. If you boss says "We don't
need a github account anymore". Then you delete the account but keep the subdomain. A hacker can create a new github with the
same github account. Then the DNS entry will point to the hacker github so my code my rules. This is completely untraceable.



# How to protect your website

![dns](/dnsmeme.jpg)

CHECK YOUR DNS RECORDS. Don't leave any emtpy DNS records.

---
title: "Uptime Kuma"
date: 2022-10-07T14:18:28-05:00
draft: false
tags: ["Self-Hosted", "tech", "hardware"]
---

# uptime-kuma


# UPTIME-KUMA

What is Uptime-Kuma? Uptime-Kuma is a self-hosted monitoring tool. I will say at first I thought this was dumb. Why would I need a uptime monitor system? When I run it just to give it a chance I fell in love with it because of one feature. The feature notification. You can send notification to email, discord, telegram, and etc.

## What are the ways to install it.

You can install using docker, install script, or build it. I use docker because I love docker. I will do an article on it later.

### How do you install it

I will show how to install it using docker. You can install [docker](https://docs.docker.com/engine/install/debian/). Then use `docker run -d --restart=always -p 3001:3001 -v uptime-kuma:/app/data --name uptime-kuma louislam/uptime-kuma:1`

Once it is up and ready if you have never docker I would give about a minutes. You can check the logs if you want to.

### Set up uptime-kuma

You need to go to your server ip like this http://10.10.10.250:3001. One you are there you should see something like this

![dashboard"](/uptime-dash.png)

Then click on "Add New Monitor".

![add](/uptime-monitor.png)

The monitoring type: http/https is a website you want to monitor, TCP port is a port you want to monitor, ping is when you just want to ping a server, and dns request of the machine.I am going to do ping. You need to set a friendly name. This is the name you will see in Uptime Kuma. Hostname is the ip of machine you want to monitor. Then just click save. You are done but we will setup email.

### Setting up email with Uptime Kuma

Click on setting up notifications.The on notification type and find Email(SMTP). It should look like this.

![email](/uptime-email.png)

Then set it up I can not tell you this because every email server is different but I will give you an example.

![setup](https://rebootcyber.xyz/images/uptime-email-set.png)

Once this is set then you should be sent emails when the machine you are monitoring goes down.

### The closing

I would recommend you playing around with Uptime Kuma.

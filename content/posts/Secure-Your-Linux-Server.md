---
title: "Secure Your Linux Server"
date: 2022-11-24T11:59:19-06:00
draft: false
tags: ["Networking", "use"]
---


GNU/Linux server are great, cost-effective way for businesses to store and share data. GNU/Linux is open-sources, so it provides plenty of resources and community cooperation
. However, that also brings security  concerns.


If you're going to run a GNU/Linux server, you NEED to know how to secure it properly.



# 1. Updates the server
The first thing you used do is update the OS to the latest version. Most VPS or cloud-based server update when you deploy them but still update. Run this commands based on the OS you are
running. If you don't know then run: ' cat /etc/issue `. This will tell you.

Debian based(Debian/Ubuntu): `sudo apt update && sudo apt upgrade `

Red Hat(CentOS): `sudo dnf upgrade `

OpenSuse: ` sudo zypper update && sudo zypper up `

# 2. Securing ssh
SSH or Secure Shell is a way to connect to your server remotely. This is really easy to secure.

## Changing port number

First you want to change the default port. This is not really a big secure step and if you want to skip it you can. If you do want to change first you go into the config file

` sudo vim /etc/ssh/sshd_config `.

Ones you do that find the line that says **Port 22** and change the 22 to something different. Make sure the number you picked is not already in used or will be used as a port number.

## SSH keys

Next we will set up a key pair. If you use GNU/Linux on your host machine (The machine you are using right now) just run

`ssh-key -t rsa `.

If you are using something different just look up generate ssh key pair with then what ever program you are using. During the create progress just add all of your info and if you want to use a password with it. For extra security I would recommend adding a password but you don't have to.

### Copying the key to the remote machine

Type

` ssh-copy-id username@your_host_address `.

Next Disable server ssh root login. Just run

` sudo vim /etc/ssh/sshd_config `

Find the line that says **PermitRootLogin_yes** and change it to **PermitRootLogin_no**. It is very important to add the user account you will use to login. Just add the line "AllowUsers your_username_here" in the sshd config file.

## Disable Empty password
You need to prevent remote logins from accounts with empty password just do

` sudo vim /etec/sshd/sshd_config `

And change the line

` PermitEmptyPasswords no `


### Disable root login
You don't need root using ssh. **Make sure that you have an account with sudo permissions before doing this**. You also have to add the user to the ssh group.

If you are on debian run ` sudo usermod -aG ssh Your_Username_here`.

` sudo vim /etc/sshd/sshd_config `

Then the line **#PermitRootLogin** and change it to

`PermitRootLogin no`

Then ssh is final secure and really locked down.



## restarting the SSH services


Then restart theSSH services. It is different for every system but if you are using systemd do

` sudo systemctl reload sshd`.

You also have to add the user to the ssh group. If you are on debian run ` sudo usermod -aG ssh Your_Username_here`.




# 3. Firewall
You need to setup firewall. This will block traffic based on the config. There are alot of firewall app on GNU/Linux but I will use UFW. Just run `sudo ufw allow SSH_Port_Number`. Then you
are done.

---
title: "IP Address"
date: 2022-11-05T11:10:02-05:00
draft: false
tags: [Networking, tech]
---

# What is a IP Address?
An IP address is Internet Protocol Address. Basically it is the address to a computer. There are two types IPv4 and IPv6. IPv4 is used everywhere but is every old. IPv6 is not used every much but is newer.


## IPv4
An IPv4 address looks like 127.0.0.1. It is kinda of a complete technology to understand. So there is public and private address. Do to some compact math there are only 4 billion IPv4 address in the world but there are 16 billion internet facing devices in the world. I may suck at math but 16 is bigger than 4.


You may be asking how do I have so many devices that can access the internet if we ran out of address. Well that is a cool technology called NAT(Network Address Translation)  it’s a way to map multiple local private addresses to a public one before transferring the information.



### NAT
There are multiply type of NAT and they are:

1. Static NAT

When the local address is converted to a public one, this NAT chooses the same one. This means there will be a consistent public IP address associated with that router or NAT device.


2. Dynamic NAT

Instead of choosing the same IP address every time, this NAT goes through a pool of public IP addresses. This results in the router or NAT device getting a different address each time the router translates the local address to a public address.



3. PAT

PAT stands for port address translation. It’s a type of dynamic NAT, but it bands several local IP addresses to a singular public one. Organizations that want all their employees’ activity to use a singular IP address use a PAT, often under the supervision of a network administrator.


### The different between public and private IPv4 address
So public address are just give out and they look like this 207.148.23.122. Will private address are special address. So Internet Corporation for Assigned Names and Numbers(Icann) said that you could not use certain address for public address and they are
1. 10.0.0.0 – 10.255.255.255
2. 172.16.0.0 – 172.31.255.255
3. 192.168.0.0 – 192.168.255.255
This are class A, B, and C address. There are some other type of Address but I will not cover them in this post.



## IPv6
This address look like this 2001:0db8:0000:0000:0000:8a2e:0370:7334. There are 340,282,366,920,938,463,463,374,607,431,768,211,456 addresses. That is a lot more than IPv4 has. The reson we don't use it is that it would take a lot of effort to move to IPv6 and I guess if it is not broken do not fix it. When give address you use DHCPv6 instead of DHCP. There is also type of IPv6 address:

1. Unicast

The Unicast address type is probably the most important one. It distinguishes itself by these sub-type addresses:

    Global Unique Addresses: Globally reachable. Examples:

2001:581:f3d1:241f::/64

2a01:388:3d11:f124::/64

    Link-local addresses: Required on every IPv6-enabled interface, but packets cannot leave or enter the interface. This address is mostly used by software applications and starts with:

fe80::/10

 Site-local addresses: Deprecated, see (RFC 3879)[https://www.rfc-editor.org/info/rfc3879].
    Loopback address: This is the address we know as 127.0.0.1/8 in IPv4, and it is written as follows in IPv6:

::1/128

Unique local addresses: Routable only within the scope of the organization. These addresses are not routable globally. IPv4 equivalent private ranges are 10.0.0.0/8, 192.168.1.0/24, and so on. Unique local addresses in IPv6 start with:

fc00::/7



2. Multicast
Multicast is the technique used to send a packet from one source (or multiple sources) to multiple destinations (receivers). In its simplest form, a multicast flow is as follows. First, a host sends an ICMPv6 packet (host solicitation) to the router(s) multicast group. Then, a router responds to this request and sends a Router Advertisement (RA) packet back to the client along with configuration parameters:
![mutlicast](/Multicast.png)

The multicast address range is ff00::/8. The first 8 bits are always ff (in binary 1111 1111).


1. Anycast

The Anycast address behaves similarly to the Multicast address, except for the following. A packet sent from a client goes to a single selected destination and not to the whole group identified by the same destination address. The receiving endpoint is selected based on the least expensive routing metric. The router uses the equal-cost multi-path to do this:


![Anycast](/Anycast.png)

Eventually, we will all be using IPv6. The sooner you understand how this address space works, and how to implement IPv6 in your own networks, the better.



## Conclusion
This are the basic of IP address I know it look compacted but just keep at it and you will get it.

---
id: 454
title: How to use nmap to scan the network for live hosts CentOS/RHEL
date: 2014-03-12T21:29:36+01:00
author: Johan Sörell
layout: revision
guid: http://geekcorner.sitedevelopments.net/2014/03/12/444-revision-v1/
permalink: /?p=454
---
This is a Junior Linux System Administrator how-to describing how you use nmap to scan for live devices within a network.

Use nmap to scan alive hosts in the network range with the command:

<pre class="lang:default decode:true">nmap -sP subnet/netmask</pre>

<pre class="lang:default decode:true">[c-johsor@sesstl168 ~]$ nmap -sP 192.168.33.0/24

Starting Nmap 5.51 ( http://nmap.org ) at 2014-03-12 22:12 CET
Nmap scan report for dlinkrouter (192.168.33.1)
Host is up (0.0023s latency).
Nmap scan report for 192.168.33.2
Host is up (0.0065s latency).
Nmap scan report for 192.168.33.130
Host is up (0.00027s latency).
Nmap done: 256 IP addresses (3 hosts up) scanned in 2.42 seconds
[c-johsor@sesstl168 ~]$</pre>

The result shows that from 256 IP addresses 3 hosts is currently up and the scan took 2.42 seconds

&nbsp;
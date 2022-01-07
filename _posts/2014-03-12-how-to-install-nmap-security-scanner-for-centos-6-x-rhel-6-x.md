---
id: 472
title: How to install nmap security scanner for CentOS 6.x / RHEL 6.x
date: 2014-03-12T23:39:03+01:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=472
permalink: /2014/03/12/how-to-install-nmap-security-scanner-for-centos-6-x-rhel-6-x/
categories:
  - CentOS
  - Linux
  - RHEL
tags:
  - CentOS
  - Install
  - Junior
  - nmap
  - nmap version 5.51
  - RHEL
---
This is an early junior System Administrator guide to install nmap security scanner. That we will use for the upcoming nmap tutorials.

This is a how to that installs the old version nmap 5.51 go to the yum totorial [How to create a local yum repo CentOS 6.x / RHEL 6.x](http://geekcorner.sitedevelopments.net/2014/03/13/how-to-create-a-local-yum-repo-centos-6-x-rhel-6-x/ "How to create a local yum repo CentOS 6.x / RHEL 6.x") to learn how to install nmap 6.40-1

Just run the command:

<pre>sudo yum install nmap -y</pre>

<pre class="lang:default decode:true">[c-johsor@sesstl168 tmp]$ sudo yum install nmap -y
Loaded plugins: fastestmirror, refresh-packagekit, security
Existing lock /var/run/yum.pid: another copy is running as pid 8746.
Another app is currently holding the yum lock; waiting for it to exit...
The other application is: PackageKit
Memory : 35 M RSS (1.4 GB VSZ)
Started: Thu Mar 13 00:29:53 2014 - 00:05 ago
State : Sleeping, pid: 8746
Loading mirror speeds from cached hostfile
* base: ftp.availo.se
* extras: ftp.availo.se
* updates: mirror.easyspeedy.com
Setting up Install Process
Resolving Dependencies
--&gt; Running transaction check
---&gt; Package nmap.x86_64 2:5.51-3.el6 will be installed
--&gt; Finished Dependency Resolution

Dependencies Resolved

========================================================================================================================================================================
Package Arch Version Repository Size
========================================================================================================================================================================
Installing:
nmap x86_64 2:5.51-3.el6 base 2.7 M

Transaction Summary
========================================================================================================================================================================
Install 1 Package(s)

Total download size: 2.7 M
Installed size: 9.7 M
Downloading Packages:
nmap-5.51-3.el6.x86_64.rpm | 2.7 MB 00:00
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
Installing : 2:nmap-5.51-3.el6.x86_64 1/1
Verifying : 2:nmap-5.51-3.el6.x86_64 1/1

Installed:
nmap.x86_64 2:5.51-3.el6

Complete!
[c-johsor@sesstl168 tmp]$</pre>

<pre class="lang:default decode:true" title="Check version of nmap">[c-johsor@sesstl168 tmp]$ nmap -version

Nmap version 5.51 ( http://nmap.org )
[c-johsor@sesstl168 tmp]$</pre>

Finished

These are the nmap tutorials up to date:  
<ul class = "posts-by-tag-list">

<li class="posts-by-tag-item CentOS Junior nmap Redhat RHEL wget" id="posts-by-tag-item-523">
  <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2014/03/13/download-latest-nmap-from-nmap-org-to-use-in-local-repo-how-to-centos-6-x-rhel-6-x/">Download latest nmap from nmap.org to use in local repo how to CentOS 6.x / RHEL 6.x</a>
</li>
<li class="posts-by-tag-item CentOS Junior nmap nmap version 6.40 Redhat RHEL yum" id="posts-by-tag-item-486">
  <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2014/03/13/how-to-create-a-local-yum-repo-centos-6-x-rhel-6-x/">How to create a local yum repo CentOS 6.x / RHEL 6.x</a>
</li>
<li class="posts-by-tag-item CentOS Install Junior nmap nmap version 5.51 RHEL" id="posts-by-tag-item-472">
  <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2014/03/12/how-to-install-nmap-security-scanner-for-centos-6-x-rhel-6-x/">How to install nmap security scanner for CentOS 6.x / RHEL 6.x</a>
</li>
<li class="posts-by-tag-item CentOS Command explained Junior network nmap Redhat RHEL scan" id="posts-by-tag-item-444">
  <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2014/03/12/how-to-use-nmap-to-scan-the-network-for-live-hosts-centosrhel/">How to use nmap to scan the network for live hosts CentOS/RHEL</a>
</li></ul>

&nbsp;

&nbsp;

&nbsp;
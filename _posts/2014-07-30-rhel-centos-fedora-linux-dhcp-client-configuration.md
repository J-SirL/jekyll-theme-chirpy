---
id: 685
title: RHEL / CentOS / Fedora Linux DHCP Client Configuration
date: 2014-07-30T18:32:19+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=685
permalink: /2014/07/30/rhel-centos-fedora-linux-dhcp-client-configuration/
categories:
  - CentOS
  - Fedora
  - Linux
  - RHEL
  - Uncategorized
tags:
  - CentOS
  - DHCP
  - Fedora
  - RHEL
---
This is a quick guide to configure the DHCP Clinent for RHEL / CentOS / Fedora.  
I&#8217;m using CentOS 6.5

RHEL / CentOS / Fedora Linux DHCP Client Configuration  
Open configuration file, enter:

<pre class="lang:default decode:true"># vi /etc/sysconfig/network-scripts/ifcfg-eth0</pre>

Append hostname, enter:

<pre class="lang:default decode:true ">DHCP_HOSTNAME=ComputerName</pre>

Save and close the file. Restart network service:

<pre class="lang:default decode:true "># service network restart</pre>

Please refer to dhclient.conf man page for more information, enter:

<pre class="lang:default decode:true ">$ man dhclient.conf</pre>

The above information is Pasted from [http://www.cyberciti.biz/faq/howto-get-linux-static-dhcp-address](http://www.cyberciti.biz/faq/howto-get-linux-static-dhcp-address "Cyberciti.biz")
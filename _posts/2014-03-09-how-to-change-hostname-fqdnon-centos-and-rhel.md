---
id: 324
title: 'How to change hostname &#8220;FQDN&#8221; on CentOS and RHEL'
date: 2014-03-09T00:55:04+01:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=324
permalink: /2014/03/09/how-to-change-hostname-fqdnon-centos-and-rhel/
categories:
  - CentOS
  - Linux
  - RHEL
tags:
  - CentOS
  - FQDN
  - Fully qualified domain name
  - Linux
  - Redhat
  - RHEL
---
This is how you change the hostname of you CentOS or Red Hat Enterprise host.

1. First check what the current fully qualified domain name is with the command hostname -f

<pre class="toolbar:1 nums:false lang:default decode:true">hostname -f</pre>

Result of the command:

<pre class="toolbar:1 nums:false wrap:true lang:default decode:true">$ hostname -f
hostname: Unknown host</pre>

In my example I will change the hostname to geekcorner at my domain sitedevelopments.net

2. edit&nbsp; /ectc/hosts and change it from localhost to your desired hostname

<pre class="toolbar:1 nums:false lang:default decode:true">sudo vi /etc/hosts</pre>

My original **/etc/hosts** looks like this:

<pre class="toolbar:1 nums:false wrap:true lang:default decode:true">#This is the original hosts file located in /etc/hosts
127.0.0.1 localhost.localdomain localhost
::1 localhost6.localdomain6 localhost6</pre>

Change the file /**etc/hosts** to what you like your hostname to be.

<pre class="toolbar:1 nums:false whitespace-after:1 lang:default decode:true">#We change it to this "If you have static IP then you can specify the IP adress to the host aswell"
127.0.0.1 geekcorner.sitedevelopments.net geekcorner    localhost.localdomain localhost
::1             localhost6.localdomain6 localhost6</pre>

3. Next we change **/etc/sysconfig/network**

<pre class="toolbar:1 nums:false lang:default decode:true">sudo vi /etc/sysconfig/network</pre>

<pre class="toolbar:1 nums:false lang:default decode:true">#This is the original /etc/sysconfig/network file
NETWORKING=yes
NETWORKING_IPV6=no
HOSTNAME=localhost
NTPSERVERARGS=iburst
~       
~  
~
"/etc/sysconfig/network" 4L, 97C</pre>

<pre class="toolbar:1 nums:false lang:default decode:true">#Change the file /etc/sysconfig/network to this
NETWORKING=yes
NETWORKING_IPV6=no
HOSTNAME=geekcorner #Change to your desired hostname
NTPSERVERARGS=iburst
~       
~  
~
"/etc/sysconfig/network" 4L, 97C</pre>

4. Restart the network.

<pre class="toolbar:1 nums:false whitespace-before:1 whitespace-after:1 lang:default decode:true">sudo service network restart</pre>

5. Check that the hostname change went well

<pre class="toolbar:1 nums:false whitespace-before:1 whitespace-after:1 lang:default decode:true">hostname -f</pre>

<pre class="toolbar:1 nums:false wrap:true whitespace-before:1 whitespace-after:1 lang:default decode:true">#You should get a reply like this:
$ hostname -f
$ geekcorner.sitedevelopments.net #this will show your Fully qualified domain name (FQDN)</pre>

Sometimes you have to restart to get the changes

<pre class="toolbar:1 nums:false whitespace-before:1 whitespace-after:1 lang:default decode:true">sudo shutdown -r now</pre>

&nbsp;

&nbsp;
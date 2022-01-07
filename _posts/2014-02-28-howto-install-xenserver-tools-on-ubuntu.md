---
id: 287
title: 'HowTo: Install XenServer Tools on ubuntu'
date: 2014-02-28T14:52:57+01:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=287
permalink: /2014/02/28/howto-install-xenserver-tools-on-ubuntu/
categories:
  - Ubuntu
  - XenServer
tags:
  - Tools
  - Ubuntu
  - XenServer
---
## Install the XenServer Tools on ubuntu

1. Put the xs-tools.iso in the virtual DVD..

2. Log in to the vm via the console or SSH

3. Create a dir called xs-tools under /mn/

<pre class="toolbar:2 nums:false lang:default decode:true" title="Make directory xs-tools under /mnt/">sudo mkdir /mnt/xs-tools</pre>

4. Mount the XenServer Tool iso to Linux

<pre class="toolbar:2 nums:false lang:default decode:true" title="Mount the XenTools ISO ">sudo mount /dev/xvdd /mnt/xs-tools</pre>

5. Go to the linux dir on the mounted iso

<pre class="toolbar:2 nums:false lang:default decode:true" title="Go to the Linux Directory">cd /mnt/xs-tools/Linux/</pre>

6. Check version of the utilities

<pre class="toolbar:2 nums:false lang:default decode:true title=" check="" the="" version="" of="" utilities="">ls -l | grep .deb</pre>

You will se something like this:

<pre class="toolbar:2 nums:false nums-toggle:false lang:default decode:true">Linux$ ls -l | grep .deb
dr-xr-xr-x 2 root root  2048 May 25  2013 debian-lenny
-r--r--r-- 1 root root   150 Nov 28 15:57 versions.deb
-r--r--r-- 1 root root 53484 Nov 28 15:57 xe-guest-utilities_6.2.0-1133_amd64.deb
-r--r--r-- 1 root root 53486 Nov 28 15:57 xe-guest-utilities_6.2.0-1133_i386.de</pre>

7. Check if you are running 32bit or 64 bit

<pre class="toolbar:2 nums:false lang:default decode:true">uname -i
x86_64</pre>

As you see I&#8217;m running 64 bit.  
7. To Install the 64 bit package type:

<pre class="toolbar:2 nums:false lang:default decode:true title=" to="" install="" type:="">sudo dpkg -i xe-guest-utilities_6.2.0-1133_amd64.deb</pre>

if you have the 32 bit version then you should install the 32 bit package

<pre class="toolbar:2 nums:false nums-toggle:false lang:default decode:true">sudo dpkg -i xe-guest-utilities_6.2.0-1133_i386.de</pre>

Now you have the xenserver tools installed to your ubuntu machine
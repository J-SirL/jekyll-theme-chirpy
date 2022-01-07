---
id: 190
title: 'How to install XenServer Tools &#8211; Linux'
date: 2013-04-16T14:03:32+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=190
permalink: /2013/04/16/how-to-install-xenserver-tools-linux/
categories:
  - XenServer
tags:
  - Install
  - Linux
  - Tools
  - XenServer
---
## Install the XenServer Tools on Linux

1. Put the xs-tools.iso in the virtual dvd..

2. Log in to the vm via the console or SSH

3. Create a dir called xs-tools under /mnt/

<pre class="lang:default decode:true" title="Make directory xs-tools under /mnt/">mkdir /mnt/xs-tools</pre>

4. Mont the XenServer Tool iso to Linux. observer

<pre class="lang:default decode:true" title="Mount the XenTools ISO ">mount /dev/xvdd /mnt/xs-tools</pre>

sometime the system has **/dev/cdrom** please use that instead.

5. Go to the linux dir on the mounted iso

<pre class="lang:default decode:true" title="Go to the Linux Directory">cd /mnt/xs-tools/Linux/</pre>

6. To Install type:

<pre class="lang:default decode:true" title="Install the XenServer Tools">bash install.sh</pre>

You will get a question if you like to continue just Answer Y

When it&#8217;s complete there will be a text saying:  
You should now reboot this Virtual Machine.  
7. Reboot..

Now you have the XenServer Tools installed
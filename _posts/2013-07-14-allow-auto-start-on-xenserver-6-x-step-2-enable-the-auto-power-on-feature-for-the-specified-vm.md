---
id: 214
title: 'Allow Auto Start on XenServer 6.x Step 2: Enable the auto power on feature for the specified VM'
date: 2013-07-14T19:08:17+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=214
permalink: /2013/07/14/allow-auto-start-on-xenserver-6-x-step-2-enable-the-auto-power-on-feature-for-the-specified-vm/
categories:
  - Virtualization
  - XenServer
tags:
  - 6.x
  - Auto-start
  - Autostart
  - Virtualization
  - XenServer
---
## Setting the Virtual Machines to Auto-Start

Gather the UUID’s of the Virtual Machine you want to auto-start by typing:

<pre class="theme:terminal nums:false nums-toggle:false wrap-toggle:false lang:sh decode:true" title="xe command to list vm:">xe vm-list</pre>

Note: This generates a list of Virtual Machines in your pool or server and their associated UUID’s.  
Copy the UUID of the Virtual Machines you want to auto-start, and type the following command for each Virtual Machine to auto-start:

<pre class="theme:terminal nums:false lang:sh decode:true" title="xe command to enable auto power on feature for the specified VM">xe vm-param-set uuid=UUID other-config:auto_poweron=true</pre>

Note:  **Replace UUID with the UUID of the Virtual Machine to auto-start.**

Repeat for all vn&#8217;s you like to autostart.

**Important to switch this off** if you are going to use **HA, DR and Pool upgrade functionality** because the auto-start function interfered with **High Availability , Disaster Recovery and Pool upgrade**.
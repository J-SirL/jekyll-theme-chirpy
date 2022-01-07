---
id: 208
title: 'Allow Auto Start on XenServer 6.x Step 1: Enable the auto power on feature at pool level'
date: 2013-07-14T18:53:16+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=208
permalink: /2013/07/14/allow-auto-start-on-xenserver-6-x-step-1-enable-the-auto-power-on-feature-at-pool-level/
categories:
  - Virtualization
  - XenServer
tags:
  - Auto Power On
  - Auto-start
  - Autostart
  - Virtualization
  - XenServer
---
## Setting the XenServer pool to allow Auto-Start

Gather the UUID’s of the pools you wish to auto-start.  
To get the list of the pool’s on your XenServer type:

<pre class="theme:terminal nums:false nums-toggle:false wrap-toggle:false lang:sh decode:true" title="xe command to list pool:">xe pool-list</pre>

Copy the UUID of the pool. If you have just one server, it will still have a pool UUID as seen below:

![](data:image/png;base64,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) 

Then type the following command to set the pool or server to allow auto-start:

<pre class="theme:terminal nums:false nums-toggle:false lang:default decode:true" title="xe command to set the pool or server to allow auto-start">xe pool-param-set uuid=UUID other-config:auto_poweron=true</pre>

**Note:** \*Replacing UUID with the UUID of the XenServer or pool.\*

**Important to switch this off** if you are going to use **HA, DR and Pool upgrade functionality** because the auto-start function interfered with **High Availability , Disaster Recovery and Pool upgrade**.
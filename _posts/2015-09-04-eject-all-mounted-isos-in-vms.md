---
id: 816
title: Eject all mounted ISOs in VMs
date: 2015-09-04T00:43:38+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=816
permalink: /2015/09/04/eject-all-mounted-isos-in-vms/
categories:
  - XenServer
tags:
  - iso
  - XenServer
---
Use this command in the pool master to eject all mounted ISOs in VMs

<pre class="lang:default decode:true " title="eject all ISOs">xe vm-cd-eject --multiple</pre>

&nbsp;
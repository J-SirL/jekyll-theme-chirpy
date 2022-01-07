---
id: 27
title: Add local storage to a XenServer
date: 2013-03-29T13:46:05+01:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=27
permalink: /2013/03/29/add-local-storage-to-a-xenserver/
image: http://media.sitedevelopments.net/2013/03/xencenter-1000x288.png
categories:
  - Virtualization
  - XenServer
tags:
  - Add
  - Local
  - Storage
  - Virtualization
  - XenServer
---
You have installed your XenServer 6.x and want to use local storage?

Log in to the shell either go to xenserver console in XenCenter or access the server via SSH. (On windows you can use putty or even better MTPuTTY &#8220;Multi-Tabbed-PuTTY&#8221;)

when your logged in to the xenserver type the following comand to check your installed disks.

type: fdisk -l

You should now see your available disks.[<img loading="lazy" class="alignright size-full wp-image-33" alt="fdisk -l" src="http://media.sitedevelopments.net/2013/03/fdisk-l.png" width="900" height="485" srcset="http://media.sitedevelopments.net/2013/03/fdisk-l.png 900w, http://media.sitedevelopments.net/2013/03/fdisk-l-300x161.png 300w, http://media.sitedevelopments.net/2013/03/fdisk-l-500x269.png 500w, http://media.sitedevelopments.net/2013/03/fdisk-l-800x431.png 800w" sizes="(max-width: 900px) 100vw, 900px" />](http://media.sitedevelopments.net/2013/03/fdisk-l.png)

In my case I have two disks that I need to install

/dev/sda and /dev/sdc

To be able to use the drive type: _pvcreate <device name>_ .  So in my case it is:

_pvcreate /dev/sda_  
[root@xenghetto ~]# pvcreate /dev/sda  
Physical volume &#8220;/dev/sda&#8221; successfully created

[root@xenghetto ~]# pvcreate /dev/sdc  
Physical volume &#8220;/dev/sdc&#8221; successfully created

Last step is to configure them for xenserver use as local storage and give them a label: _xe sr-create type=lvm content-type=user device-config:device=/dev/disk/by-id/dev/sdc name-label=”Local Disk 2”_

_xe sr-create type=lvm content-type=user device-config:device=/dev/disk/by-id/dev/sda name-label=”Local Disk 3”_

Now you see your disks in XenCenter.

Enjoy..
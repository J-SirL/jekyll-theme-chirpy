---
id: 45
title: Remove local storage XenServer 6.x
date: 2013-03-29T13:46:35+01:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=45
permalink: /2013/03/29/remove-local-storage-xenserver-6-x/
categories:
  - Virtualization
tags:
  - Detach
  - Local
  - Remove
  - Storage
  - XenServer
---
This time I&#8217;ll show you how to remove local storage from your XenServer 6.x host.

## 1. log in to your xenserver host via ssh

Use your favourite SSH program I prefer using  MTPuTTY myself.

## 2.List your storage repositories.

type **xe sr-list** to get the **UUID** from the local share you want to remove.

You will see something like this:

**uuid** ( RO) : 62aac8ce-f974-9ecc-5a6f-6e601fcef97a  
**name-label** ( RW): Local storage  
name-description ( RW):  
host ( RO): xenghetto.sitedevelopments.local  
type ( RO): lvm  
content-type ( RO): user

**uuid** string is the Storage Repository uuid (SR-uuid) that you need to be able to do the next step.

**name-label** This is the name of the local storage so check if that corresponds to the local storage you want to detach before you go to the next step.

## **Step 3. Get the Physical Block Device UUID.**

Now it&#8217;s time to get the Physical Block Device (PBD):

You find that by typing:  xe pbd-list sr-uuid=Your-UUID

[root@xenghetto # **xe pbd-list sr-uuid=62aac8ce-f974-9ecc-5a6f-6e601fcef97a**  
uuid ( RO)                  : 47127040-7e77-749c-ce24-49d33b9df232  
host-uuid ( RO): 4b3c5ae2-6b22-4972-bea5-9467b25f519d  
sr-uuid ( RO): 62aac8ce-f974-9ecc-5a6f-6e601fcef97a  
device-config (MRO): device: /dev/disk/by-id/scsi-SATA\_INTEL\_SSDSC2CT0CVMP2156091M060AGN-part3  
currently-attached ( RO): true

**uuid ( RO)** This is the PBD-uuid write this down and lets unplug the local storage.

## Step 4. Unplug the local storage.

To unplug the local storage you type the following:

xe pbd-unplug uuid=Your-PBD-uuid

In my case it&#8217;s:

xe pbd-unplug uuid=**47127040-7e77-749c-ce24-49d33b9df232**

it should now be unplugged. you can check that in xencenter.

## Step 5.Delete the PBD:

xe pbd-destroy uuid=your-PBD-uuid

in my case it&#8217;s

xe pbd-destroy uuid=47127040-7e77-749c-ce24-49d33b9df232

if you go to xencenter you will now see that it&#8217;s fully detached:[<img loading="lazy" class="size-medium wp-image-61 alignleft" alt="detached localstorage" src="http://media.sitedevelopments.net/2013/03/localstorage-detached-300x175.png" width="300" height="175" srcset="http://media.sitedevelopments.net/2013/03/localstorage-detached-300x176.png 300w, http://media.sitedevelopments.net/2013/03/localstorage-detached-500x293.png 500w, http://media.sitedevelopments.net/2013/03/localstorage-detached.png 687w" sizes="(max-width: 300px) 100vw, 300px" />](http://media.sitedevelopments.net/2013/03/localstorage-detached.png)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

## 6. Forget ( remove ) the Local storage from showing up as detached.

xe sr-forget uuid=your-SR-uuid

xe sr-forget uuid=62aac8ce-f974-9ecc-5a6f-6e601fcef97a

Now check your XenCenter that it&#8217;s removed.

[<img loading="lazy" class="size-full wp-image-65 alignleft" alt="done-removing-localstorage" src="http://media.sitedevelopments.net/2013/03/done-removing-localstorage.png" width="231" height="112" />](http://media.sitedevelopments.net/2013/03/done-removing-localstorage.png)

&nbsp;

&nbsp;
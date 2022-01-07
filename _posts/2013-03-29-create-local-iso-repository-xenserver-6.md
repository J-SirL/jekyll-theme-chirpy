---
id: 84
title: Create local ISO repository XenServer 6
date: 2013-03-29T19:43:01+01:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=84
permalink: /2013/03/29/create-local-iso-repository-xenserver-6/
categories:
  - Virtualization
  - XenServer
tags:
  - Add
  - Create
  - iso
  - Local
  - Repository
  - XenServer
---
This time I&#8217;ll show you how to create local ISO repository for your XenServer 6 host.

### First let&#8217;s check the available disk space

You do that with the df command:** **

<pre class="theme:terminal nums:false lang:default decode:true" title="df -h">df -h</pre>

Read more about the  <a title="Permanent Link to df [Command]" href="http://linuxconfig.net/commands/command-df.html" rel="bookmark">df [Command]</a>

[<img loading="lazy" class="alignleft size-full wp-image-85" alt="df -h is the command to check disk space" src="http://media.sitedevelopments.net/2013/03/df-h-checkspacebefore-iso.png" width="453" height="96" srcset="http://media.sitedevelopments.net/2013/03/df-h-checkspacebefore-iso.png 453w, http://media.sitedevelopments.net/2013/03/df-h-checkspacebefore-iso-300x63.png 300w" sizes="(max-width: 453px) 100vw, 453px" />](http://media.sitedevelopments.net/2013/03/df-h-checkspacebefore-iso.png)

As you see there is not a lot of space available for an ISO repository on /dev/sdb1

### Let&#8217;s create  a new Logical Volume (LV)

To do this we need to check the available physical disk space:

Type the following to check available physical disk space

<pre class="theme:terminal nums:false lang:sh decode:true" title="To check available physical disk space type pvs">pvs</pre>

&nbsp;

[<img loading="lazy" class="alignleft size-full wp-image-91" alt="pvs output" src="http://media.sitedevelopments.net/2013/03/pvs-output.png" width="622" height="79" srcset="http://media.sitedevelopments.net/2013/03/pvs-output.png 622w, http://media.sitedevelopments.net/2013/03/pvs-output-300x38.png 300w" sizes="(max-width: 622px) 100vw, 622px" />](http://media.sitedevelopments.net/2013/03/pvs-output.png)

I am going to use  /dev/sdb3 VG_XenStorage-62aac8ce-f974-9ecc-5a6f-6e601fcef97a

### Now lets check the Volume Group(s) (VG):

Type vgs to check the Volume Group(s)****

<pre class="theme:terminal nums:false lang:sh decode:true">vgs</pre>

&nbsp;

[<img loading="lazy" class="alignleft size-full wp-image-108" alt="vgs output" src="http://media.sitedevelopments.net/2013/03/vgs-output.png" width="608" height="81" srcset="http://media.sitedevelopments.net/2013/03/vgs-output.png 608w, http://media.sitedevelopments.net/2013/03/vgs-output-300x39.png 300w" sizes="(max-width: 608px) 100vw, 608px" />](http://media.sitedevelopments.net/2013/03/vgs-output.png)

&nbsp;

###  Let&#8217;s create the new LV in the Volume Group

I have decided to create a 20G ISO storage for my server so let&#8217;s create the new LV.

Type: lvcreate -L 20G -n isoImages And your VG_XenStorage****

<pre class="theme:terminal nums:false lang:default decode:true" title="Create a 20G Logical Volume called isoImages">lvcreate -L 20G -n isoImages VG_XenStorage-62aac8ce-f974-9ecc-5a6f-6e601fcef97a</pre>

&nbsp;

[<img loading="lazy" class="alignleft size-full wp-image-116" alt="lvcreate output" src="http://media.sitedevelopments.net/2013/03/lvcreate-output.png" width="702" height="42" srcset="http://media.sitedevelopments.net/2013/03/lvcreate-output.png 702w, http://media.sitedevelopments.net/2013/03/lvcreate-output-300x17.png 300w" sizes="(max-width: 702px) 100vw, 702px" />](http://media.sitedevelopments.net/2013/03/lvcreate-output.png)

&nbsp;

### Create filesystem on our newly created Logical Volume (LV)

type mkfs.ext3 /dev/**And your VG_XenStorage**

<pre class="theme:terminal nums:false lang:sh decode:true" title="The command mkfs.ext3 ">mkfs.ext3 /dev/sdb3 VG_XenStorage-62aac8ce-f974-9ecc-5a6f-6e601fcef97a</pre>

&nbsp;

[<img loading="lazy" class="alignleft size-full wp-image-120" alt="mkfs output" src="http://media.sitedevelopments.net/2013/03/mkfs-output.png" width="671" height="411" srcset="http://media.sitedevelopments.net/2013/03/mkfs-output.png 671w, http://media.sitedevelopments.net/2013/03/mkfs-output-300x184.png 300w" sizes="(max-width: 671px) 100vw, 671px" />](http://media.sitedevelopments.net/2013/03/mkfs-output.png)

### Create a mount point

Type the following to create isoImage under /mnt directory

<pre class="theme:terminal nums:false lang:sh decode:true" title="Create directory isoImages in directory /mnt. with mkdir /mnt/isoImages">mkdir /mnt/isoImages</pre>

### Update changes to The Volume Group

Now we must make the newly created Logical Volume in the Volume Group visible to the XenServer core system. We do that by typing:

<pre class="theme:terminal nums:false lang:sh decode:true" title="Process the Volume Group Change with vgchange -a y">vgchange -a y</pre>

###  Now it&#8217;s time to create the ISO Repository

We use the command **xe sr-create **to make the ISO Repository

<pre class="theme:terminal nums:false lang:sh decode:true" title="The command xe sr-create">xe sr-create name-label=ISOimages type=iso device-config:location=/mnt/isoImages/ device-config:legacy_mode=true content-type=iso</pre>

Let&#8217;s check the new repository listing with: **xe sr-list**

<pre class="theme:terminal nums:false lang:default decode:true" title="Output example:">uuid ( RO)                : f8c14526-f2b9-6fd3-dae4-00d111739b98
          name-label ( RW): ISOimage
    name-description ( RW):
                host ( RO): xenghetto.sitedevelopments.local
                type ( RO): iso
        content-type ( RO): iso</pre>

###  Mount the ISO Repository

<pre class="theme:terminal nums:false lang:sh decode:true" title="Mount isoImages">mount -t ext3 /dev/VG_XenStorage-62aac8ce-f974-9ecc-5a6f-6e601fcef97a/isoImages /mnt/isoImages</pre>

Edit /etc/fstab to make sure the isoImages mounts at reboot.

<pre class="theme:terminal nums:false lang:sh decode:true" title="make sure it's mounted after reboot by typing:">echo "/dev/VG_XenStorage-62aac8ce-f974-9ecc-5a6f-6e601fcef97a/isoImages /mnt/isoImages ext3 defaults 1 1" &gt;&gt; /etc/fstab</pre>

&nbsp;

[ Upload ISO&#8217;s to your ISO Repository.](http://geekcorner.sitedevelopments.net/2013/03/29/upload-isos-to-your-newly-created-iso-repository/ "Upload ISO’s to your Newly created ISO Repository")
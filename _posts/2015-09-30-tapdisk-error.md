---
id: 820
title: Tapdisk error
date: 2015-09-30T03:21:39+02:00
author: Per Jönulv
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=820
permalink: /2015/09/30/tapdisk-error/
categories:
  - XenServer
tags:
  - Error
  - tapdisk
  - XenServer
---
If you get tapdisk error in Xenserver you can check the vhd file with vhd-util

example

<pre class="lang:default decode:true ">vhd-util check -n \mounted share\uuid.vhd -p</pre>

&nbsp;

Then you will get the list of parents of the recent copy of the VM hard drive.  
If you get an error either the parent hard drive  is missing or is corrupt.  
Restore the file from backup and do the check again . if no error good ,  
if you get another parent missing restore that to and so on.

If the file is missing you have a big problem .

To list the UUID of harddrive  
use

<pre class="lang:default decode:true ">xe vdi-list | grep name</pre>

&nbsp;

The hard drives should already been merged by the  coalesce function but it could be that it fails. That&#8217;s why this could be handy for you , so add it to your bookmarks for a rainy day.

&nbsp;

&nbsp;
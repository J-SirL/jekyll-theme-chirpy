---
id: 569
title: 'Diskpart command: Change drive letter using diskpart Windows 2012 R2'
date: 2014-04-03T22:40:59+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=569
permalink: /2014/04/03/diskpart-command-change-drive-letter-using-diskpart-windows-2012-r2/
categories:
  - Windows 2012
tags:
  - Diskpart
  - Windows
---
Have you accedently got a drive letter wrong by not activating Data disk or just want to change your drive letter?  
This is how you do it with Diskpart.

Open command line:

<pre class="lang:default decode:true">cmd</pre>

Type Diskpart

<pre class="lang:default decode:true" title="Run the command Diskpart">C:\Users\Johan&gt;diskpart

Microsoft DiskPart version 6.1.7601
Copyright (C) 1999-2008 Microsoft Corporation.
Dator: STATIONT

DISKPART&gt;</pre>

List current volumes:

<pre class="lang:default decode:true" title="Output List volume">DISKPART&gt; list volume
  Volumenr 0     E                       DVD-ROM         0 B

  Volumenr 1     G                       DVD-ROM         0 B

  Volumenr 2     F                       DVD-ROM         0 B

  Volumenr 3     C   WINDOWS      NTFS   Partition    299 G

  Volymnr 4     D   Data         NTFS   Partition    296 G

  Volymnr 5         SYSTEM       NTFS   Partition    400 M

DISKPART&gt;</pre>

Select Volume:

<pre class="lang:default decode:true" title="Select the volume you like to change in my case I'll change vol 2">DISKPART&gt; select volume 2

Volume 2 is the selected volume.

DISKPART&gt;</pre>

Remove the drive letter:

<pre class="lang:default decode:true" title="Remove the letter ">DISKPART&gt; remove letter "F"

The drive letter or mount point is removed.

DISKPART&gt;</pre>

Assigne the new drive letter:

<pre class="lang:default decode:true" title="Assign the new letter">DISKPART&gt; assign letter "Q"

The drive letter or mount point is removed.

DISKPART&gt;</pre>

That was all folks

A command recap:

<pre class="lang:default decode:true" title="Diskpart command for changing drive letter on DVD or HD!">Diskpart
list volume
select volume 1 ,2,3,4,5 what ever your DCROM Drive or HD ist…
remove letter=E “for exmple”
assign letter=D “for exmple”</pre>
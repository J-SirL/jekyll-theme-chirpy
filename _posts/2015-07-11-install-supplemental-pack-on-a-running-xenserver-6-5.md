---
id: 717
title: Install supplemental pack on a running Xenserver 6.5
date: 2015-07-11T16:03:19+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=717
permalink: /2015/07/11/install-supplemental-pack-on-a-running-xenserver-6-5/
categories:
  - Virtualization
  - XenServer
tags:
  - Installation
  - supplemental pack
  - XenServer
---
## Now I will show you how you easily can install a supplemental pack on a running XenServer.

To make sure that you get the most out of your Xenserver 6.5 SP1 you should install the Container management supplemental pack so you can use Docker in you xenserver pool.

> Requirements to follow this blog post is a updated Xenserver 6.5 with SP1  
> I have XenServer version 6.5 with SP1 that I patched automagically with a script [xs_patcher](https://github.com/antonym/xs_patcher) that script has a little drawback and that&#8217;s because you need to manually add new availible patches to the script. You should perhaps test this script instead [citrix xenserver patcher](https://github.com/dalgibbard/citrix_xenserver_patcher) I haven&#8217;t tested in on xenserver 6.5.

<div data-canvas-width="752.0999999999998">
  Each supplemental pack contains an installation script. To install a pack on a XenServer host, copy it to the host
</div>

<div data-canvas-width="124.54999999999997">
  and run the script:
</div>

<pre class="lang:default decode:true " title="Mount the xscontainer iso run the script and unmount it">mkdir /tmp/iso
mount -o loop XenServer-6.5.0-SP1-xscontainer.iso /tmp/iso
cd /tmp/iso
./install.sh
cd
umount /tmp/iso</pre>

&nbsp;

<div data-canvas-width="317.98333333333335">
  is the name of the ISO file containing the pack.
</div>

<div data-canvas-width="571.8833333333332">
  Of course, it is also possible to burn the ISO to physical media, and install from there
</div>
---
id: 735
title: Dell firmware updates on xenserver 6.5
date: 2015-07-28T16:08:43+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=735
permalink: /2015/07/28/dell-firmware-updates-on-xenserver-6-5/
categories:
  - Uncategorized
  - XenServer
tags:
  - Dell
  - firmware
  - Update
---
If you are running your xenserver on Dell servers you need to install dell\_ft\_install repo

If you want firmware updates, just install the glibc.i686 from CentOS along with dell\_ft\_install:

<pre class="lang:default decode:true " title="Install  glibc.i686 and dell_ft_install">yum –-enablerepo=base,updates install glibc.i686 dell_ft_install
</pre>

&nbsp;

<pre class="lang:default decode:true " title="Install bootstrap firmware">yum install $(bootstrap_firmware)
</pre>

First you need to run update_firmware to check if there is firmware to be updated

<pre class="lang:default decode:true" title="First run update_firmware">update_firmware
</pre>

If it finds firmware to be updated you should use the &#8211;yes switch

<pre class="lang:default decode:true " title="Then you run update_firmaware --yes to update firmware">update_firmware –-yes</pre>

&nbsp;
---
id: 753
title: Generate SHA512 password with CentOS 7,FEDORA 7, RHEL 7
date: 2015-08-04T01:54:49+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=753
permalink: /2015/08/04/generate-sha512-password-with-centos-7fedora-7-rhel-7/
categories:
  - CentOS
  - Fedora
  - Linux
  - RHEL
tags:
  - CentOS
  - Fedora
  - password
  - RHEL
  - SHA512
---
If you need to generate a SHA512 encrypted password for kickstart or perhaps for bootstrapping you servers with automation tools like ansible you can do this easily with python.

<pre class="lang:default decode:true " title="Encryp password with python version 2.7 or above">python -c 'import crypt,getpass; print(crypt.crypt(getpass.getpass(), crypt.mksalt(crypt.METHOD_SHA512)))'
</pre>

If you have python below version 2.7 the you should use this command:

<pre class="lang:default decode:true " title="This command is for python below version 2.7">python -c 'import crypt; print crypt.crypt("YOURPasswordGoesHEr3", "$6$saltsalt$")'</pre>

&nbsp;
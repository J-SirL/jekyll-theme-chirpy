---
id: 656
title: How to reset the OS back to the base permissions and uid/gids
date: 2014-06-17T16:23:28+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=656
permalink: /2014/06/17/how-to-reset-the-os-back-to-the-base-permissions-and-uidgids/
categories:
  - CentOS
  - Linux
  - RHEL
tags:
  - CentOS
  - RHEL
---
If your system have been compromised RedHat has a way to reset the OS back to the base permissions and uid/gids.

This is how you do it.

Resets uids and gids on files and directories:

<pre class="lang:default decode:true">for i in $(rpm -qa); do rpm --setugids $i; done</pre>

Resets perms on dirs & files:

<pre class="lang:default decode:true">for i in $(rpm -qa); do rpm --setperms $i; done</pre>
---
id: 265
title: 'Fixing &#8220;authentication is required to set the network proxy &#8230;&#8221; on Redhat/CentOS'
date: 2014-02-27T07:38:59+01:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=265
permalink: /2014/02/27/fixing-authentication-is-required-to-set-the-network-proxy-on-redhatcentos/
categories:
  - CentOS
  - Linux
  - RHEL
tags:
  - authentication
  - CentOS
  - Error
  - PackageKit
  - Redhat
  - RHEL
  - Solution
---
Some times I have got an GUI pop-up message that says the following, and asks for the root password at login:

authentication is required to set the network proxy used for downloading packages.  An  
application is attempting to perform an action that requires privileges.  
Authentication as the super user is required to perform this action&#8221;

I have goggled it a bit but no one actually solved the problem before.

I got fed up and solved the problem my self.

This is how I did it.

First I checked what version of PackageKit I had .

To do this you type:

<pre class="toolbar:2 nums:false nums-toggle:false lang:vim decode:true">yum provides PackageKit</pre>

<pre class="theme:cisco-router font:consolas toolbar:2 nums:false nums-toggle:false show-plain-default:true lang:default decode:true">[root@test1 ~]# yum provides PackageKit
Loaded plugins: fastestmirror, security
Loading mirror speeds from cached hostfile
 * base: mirror.nsc.liu.se
 * epel: mirror.nsc.liu.se
 * extras: mirror.nsc.liu.se
 * updates: mirror.nsc.liu.se
PackageKit-0.5.8-21.el6.x86_64 : Package management service
Repo        : base
Matched from:

PackageKit-0.5.8-21.el6.x86_64 : Package management service
Repo        : installed
Matched from:
Other       : Provides-match: PackageKit</pre>

As you see above the package that I had installed were: PackageKit-0.5.8-21.el6.x86_64

I do not know if it&#8217;s necessary but I stopped vncserver and xrdp by typing

service vncserver stop | service xrdp stop.  see example below:

<pre class="toolbar:2 nums:false lang:default decode:true">service vncserver stop | service xrdp stop
Stopping xrdp: [  OK  ]
Stopping xrdp-sesman: [  OK  ]</pre>

Then I just reinstalled PackageKit by typing:

<pre class="theme:cisco-router font:consolas toolbar:2 nums:false nums-toggle:false show-plain-default:true lang:default decode:true">yum reinstall PackageKit-0.5.8-21.el6.x86_64</pre>

Then I restarted the machine because I wanted to know if it was a permanent solution.

<pre class="toolbar:2 nums:false lang:default decode:true">shutdown -r now</pre>

It wasn&#8217;t harder than that.

Enjoy the rest of my tips

Regards

Johan
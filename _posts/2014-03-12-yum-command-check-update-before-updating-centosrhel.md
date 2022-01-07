---
id: 436
title: 'Yum command: check-update before updating CentOS/RHEL'
date: 2014-03-12T20:51:19+01:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=436
permalink: /2014/03/12/yum-command-check-update-before-updating-centosrhel/
image: http://media.sitedevelopments.net/2014/03/yum-check-update.png
categories:
  - CentOS
  - Linux
  - RHEL
tags:
  - CentOS
  - Comand Line Interface
  - Command
  - explained
  - Junior
  - Redhat
  - RHEL
  - yum
---
If you like to check if there is updates and what packages that you are able to get updates of you should use the command:

<pre class="lang:default decode:true">sudo yum check-update</pre>

<pre class="lang:default decode:true">[c-johsor@sesstl168 ~]$ yum check-update
Loaded plugins: fastestmirror, refresh-packagekit, security
Determining fastest mirrors
 * base: ftp.lysator.liu.se
 * extras: ftp.lysator.liu.se
 * updates: mirror.easyspeedy.com
adobe-linux-x86_64                                                          2/2

coreutils.x86_64                       8.4-31.el6_5.1                    updates
coreutils-libs.x86_64                  8.4-31.el6_5.1                    updates
libtirpc.x86_64                        0.2.1-6.el6_5.1                   updates
upstart.x86_64                         0.6.5-13.el6_5.3                  updates</pre>

As you see coreutils have a new version.

I like to update my system so I update it with:

<pre class="lang:default decode:true">sudo yum update</pre>

<pre class="lang:default decode:true">[c-johsor@sesstl168 ~]$ sudo yum update
Loaded plugins: fastestmirror, refresh-packagekit, security
Loading mirror speeds from cached hostfile
 * base: ftp.uninett.no
 * extras: ftp.uninett.no
 * updates: mirror.academica.fi
Setting up Update Process
Resolving Dependencies
--&gt; Running transaction check
---&gt; Package coreutils.x86_64 0:8.4-31.el6 will be updated
---&gt; Package coreutils.x86_64 0:8.4-31.el6_5.1 will be an update
---&gt; Package coreutils-libs.x86_64 0:8.4-31.el6 will be updated
---&gt; Package coreutils-libs.x86_64 0:8.4-31.el6_5.1 will be an update
---&gt; Package libtirpc.x86_64 0:0.2.1-6.el6_4 will be updated
---&gt; Package libtirpc.x86_64 0:0.2.1-6.el6_5.1 will be an update
---&gt; Package upstart.x86_64 0:0.6.5-13.el6_5.2 will be updated
---&gt; Package upstart.x86_64 0:0.6.5-13.el6_5.3 will be an update
--&gt; Finished Dependency Resolution

Dependencies Resolved

================================================================================
 Package              Arch         Version                  Repository     Size
================================================================================
Updating:
 coreutils            x86_64       8.4-31.el6_5.1           updates       3.0 M
 coreutils-libs       x86_64       8.4-31.el6_5.1           updates        50 k
 libtirpc             x86_64       0.2.1-6.el6_5.1          updates        79 k
 upstart              x86_64       0.6.5-13.el6_5.3         updates       177 k

Transaction Summary
================================================================================
Upgrade       4 Package(s)

Total download size: 3.3 M
Is this ok [y/N]: y
Downloading Packages:
(1/4): coreutils-8.4-31.el6_5.1.x86_64.rpm               | 3.0 MB     00:01     
(2/4): coreutils-libs-8.4-31.el6_5.1.x86_64.rpm          |  50 kB     00:00     
(3/4): libtirpc-0.2.1-6.el6_5.1.x86_64.rpm               |  79 kB     00:00     
(4/4): upstart-0.6.5-13.el6_5.3.x86_64.rpm               | 177 kB     00:00     
--------------------------------------------------------------------------------
Total                                           2.4 MB/s | 3.3 MB     00:01     
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Updating   : coreutils-libs-8.4-31.el6_5.1.x86_64                         1/8 
  Updating   : coreutils-8.4-31.el6_5.1.x86_64                              2/8 
  Updating   : libtirpc-0.2.1-6.el6_5.1.x86_64                              3/8 
  Updating   : upstart-0.6.5-13.el6_5.3.x86_64                              4/8 
  Cleanup    : coreutils-libs-8.4-31.el6.x86_64                             5/8 
  Cleanup    : coreutils-8.4-31.el6.x86_64                                  6/8 
  Cleanup    : libtirpc-0.2.1-6.el6_4.x86_64                                7/8 
  Cleanup    : upstart-0.6.5-13.el6_5.2.x86_64                              8/8 
  Verifying  : upstart-0.6.5-13.el6_5.3.x86_64                              1/8 
  Verifying  : libtirpc-0.2.1-6.el6_5.1.x86_64                              2/8 
  Verifying  : coreutils-8.4-31.el6_5.1.x86_64                              3/8 
  Verifying  : coreutils-libs-8.4-31.el6_5.1.x86_64                         4/8 
  Verifying  : coreutils-8.4-31.el6.x86_64                                  5/8 
  Verifying  : upstart-0.6.5-13.el6_5.2.x86_64                              6/8 
  Verifying  : libtirpc-0.2.1-6.el6_4.x86_64                                7/8 
  Verifying  : coreutils-libs-8.4-31.el6.x86_64                             8/8 

Updated:
  coreutils.x86_64 0:8.4-31.el6_5.1    coreutils-libs.x86_64 0:8.4-31.el6_5.1   
  libtirpc.x86_64 0:0.2.1-6.el6_5.1    upstart.x86_64 0:0.6.5-13.el6_5.3        

Complete!
[c-johsor@sesstl168 ~]$</pre>

If you do not like to answer yes on every question just run:

<pre class="lang:default decode:true">sudo update -y</pre>

&nbsp;
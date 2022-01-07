---
id: 486
title: How to create a local yum repo CentOS 6.x / RHEL 6.x
date: 2014-03-13T20:50:10+01:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=486
permalink: /2014/03/13/how-to-create-a-local-yum-repo-centos-6-x-rhel-6-x/
categories:
  - CentOS
  - Linux
  - RHEL
tags:
  - CentOS
  - Junior
  - nmap
  - nmap version 6.40
  - Redhat
  - RHEL
  - yum
---
This is an early junior System Administrator guide:

This time I will show you how to create a local yum repository that you can use in your environment.

First you need to create a directory to host your local yum repo in.

I have decided to create two directories because I might add several local repositories in the future.

<pre class="lang:default decode:true" title="Let's create two directories so we can have more repos in the future">sudo mkdir /repostore
sudo mkdir /repostore/nmap6.40-1</pre>

Then move or copy the rpm files that you would like to have in your local yum repository.

<pre class="lang:default decode:true" title="I'm moving the nmap repo to the dir nmap6.40-1 I created earlier">Move rpm file
sudo mv nmap-6.40-1.x86_64.rpm /repostore/nmap6.40-1/
Or copy rpm file
sudo cp nmap-6.40-1.x86_64.rpm /repostore/nmap6.40-1/</pre>

Now we need to run the command createrepo:

<pre class="lang:default decode:true" title="createrepo">sudo createrepo /repostore/nmap6.40-1</pre>

<pre class="lang:default decode:true" title="output of command createrepo">[c-johsor@sesstl168 /]$ sudo createrepo /repostore/nmap6.40-1/
Spawning worker 0 with 1 pkgs
Workers Finished
Gathering worker results

Saving Primary metadata
Saving file lists metadata
Saving other metadata
Generating sqlite DBs
Sqlite DBs complete</pre>

Now we need to create the yum repo configuration file in the folder /etc/yum.repos.d/

<pre class="lang:default decode:true" title="Let's name the repo nman-version">sudo vi /etc/yum.repos.d/nmap-6.40-1.repo</pre>

<pre class="lang:default decode:true" title="Let's name the repository nmap-6.40-1 after the nmap-6.40-1.repo filename">[nmap-6.40-1]
name=Nmap Version 6.1.40-1 Local Repo
baseurl=file:///repostore/
enabled=1
gpgcheck=0</pre>

The we install the repo with the command:

<pre class="lang:default decode:true" title="yum install reponame">sudo yum install nmap-6.40-1</pre>

<pre class="lang:default decode:true" title="Installation output">[c-johsor@sesstl168 ~]$ sudo yum install nmap-6.40-1
[sudo] password for c-johsor: 
Loaded plugins: fastestmirror, refresh-packagekit, security
Loading mirror speeds from cached hostfile
 * base: mirror.searchdaimon.com
 * extras: mirror.searchdaimon.com
 * updates: mirror.academica.fi
Setting up Install Process
Resolving Dependencies
--&gt; Running transaction check
---&gt; Package nmap.x86_64 2:6.40-1 will be installed
--&gt; Finished Dependency Resolution

Dependencies Resolved

================================================================================
 Package        Arch             Version            Repository             Size
================================================================================
Installing:
 nmap           x86_64           2:6.40-1           nmap-6.40-1           4.8 M

Transaction Summary
================================================================================
Install       1 Package(s)

Total download size: 4.8 M
Installed size: 17 M
Is this ok [y/N]:</pre>

Press y/Y to continue or n/N to cancel

We continue:

<pre class="lang:default decode:true" title="Installation output after pressing y">Is this ok [y/N]: y
Downloading Packages:
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing : 2:nmap-6.40-1.x86_64                                                                                                                                 1/1 
  Verifying  : 2:nmap-6.40-1.x86_64                                                                                                                                 1/1 

Installed:
  nmap.x86_64 2:6.40-1                                                                                                                                                  

Complete!
[c-johsor@sesstl168 ~]$</pre>

Let&#8217;s run yum info nmap and check the information about nmap.

<pre class="lang:default decode:true" title="command: yum info package name">[c-johsor@sesstl168 ~]$ yum info nmap-6.40-1
Loaded plugins: fastestmirror, refresh-packagekit, security
Loading mirror speeds from cached hostfile
 * base: ftp.funet.fi
 * extras: ftp.funet.fi
 * updates: ftp.lysator.liu.se
Installed Packages
Name        : nmap
Arch        : x86_64
Epoch       : 2
Version     : 6.40
Release     : 1
Size        : 17 M
Repo        : installed
From repo   : nmap-6.40-1
Summary     : Network exploration tool and security scanner
URL         : http://nmap.org
License     : http://nmap.org/man/man-legal.html
Description : 
            : Nmap ("Network Mapper") is a free and open source utility
            : for network exploration or security auditing. Many systems and
            : network administrators also find it useful for tasks such as
            : network inventory, managing service upgrade schedules, and
            : monitoring host or service uptime. Nmap uses raw IP packets in
            : novel ways to determine what hosts are available on the network,
            : what services (application name and version) those hosts are
            : offering, what operating systems (and OS versions) they are
            : running, what type of packet filters/firewalls are in use, and
            : dozens of other characteristics. It was designed to rapidly scan
            : large networks, but works fine against single hosts. Nmap runs on
            : all major computer operating systems, and both console and
            : graphical versions are available.

[c-johsor@sesstl168 ~]$</pre>

Let&#8217;s check the version information of nmap to get more details:

<pre class="lang:default decode:true" title="nmap -version">[c-johsor@sesstl168 /]$ nmap -version

Nmap version 6.40 ( http://nmap.org )
Platform: x86_64-redhat-linux-gnu
Compiled with: liblua-5.2.2 openssl-0.9.8k nmap-libpcre-7.6 nmap-libpcap-1.2.1 nmap-libdnet-1.12 ipv6
Compiled without:
Available nsock engines: epoll poll select
[c-johsor@sesstl168 /]$</pre>

That is the end of the tutorial.

Next you can read about how to use namp by checking out the current nmap tutorials here:<ul class = "posts-by-tag-list">

<li class="posts-by-tag-item CentOS Junior nmap Redhat RHEL wget" id="posts-by-tag-item-523">
  <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2014/03/13/download-latest-nmap-from-nmap-org-to-use-in-local-repo-how-to-centos-6-x-rhel-6-x/">Download latest nmap from nmap.org to use in local repo how to CentOS 6.x / RHEL 6.x</a>
</li>
<li class="posts-by-tag-item CentOS Junior nmap nmap version 6.40 Redhat RHEL yum" id="posts-by-tag-item-486">
  <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2014/03/13/how-to-create-a-local-yum-repo-centos-6-x-rhel-6-x/">How to create a local yum repo CentOS 6.x / RHEL 6.x</a>
</li>
<li class="posts-by-tag-item CentOS Install Junior nmap nmap version 5.51 RHEL" id="posts-by-tag-item-472">
  <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2014/03/12/how-to-install-nmap-security-scanner-for-centos-6-x-rhel-6-x/">How to install nmap security scanner for CentOS 6.x / RHEL 6.x</a>
</li>
<li class="posts-by-tag-item CentOS Command explained Junior network nmap Redhat RHEL scan" id="posts-by-tag-item-444">
  <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2014/03/12/how-to-use-nmap-to-scan-the-network-for-live-hosts-centosrhel/">How to use nmap to scan the network for live hosts CentOS/RHEL</a>
</li></ul> 

Or you can check out more information about yum:<ul class = "posts-by-tag-list">

<li class="posts-by-tag-item CentOS provides Repository RHEL VirtualBox yum" id="posts-by-tag-item-705">
  <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2015/07/11/install-virtualbox-5-on-centos-7-using-virtualbox-repository/">install VirtualBox 5 on CentOS 7 using VirtualBox repository</a>
</li>
<li class="posts-by-tag-item 7.x CentOS EPEL Fedora IT automation Repository yum" id="posts-by-tag-item-698">
  <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2015/07/11/installation-instructions-to-install-ansible-with-yum-on-centos-7-x-rhel-7-x-fedora-7-x/">Installation instructions to install Ansible with yum on CentOS 7.x, RHEL 7.x, Fedora 7.x</a>
</li>
<li class="posts-by-tag-item CentOS cntlm Command ISA Linux proxy Redhat RHEL yum" id="posts-by-tag-item-590">
  <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2014/04/05/how-to-use-yum-through-isa-proxy-using-active-directory-account/">how to use yum through ISA proxy using Active Directory account</a>
</li>
<li class="posts-by-tag-item CentOS clean Command Fedora metadata RHEL yum" id="posts-by-tag-item-575">
  <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2014/04/05/how-to-fix-yum-errors-on-centos-rhel-or-fedora-distributions/">How to fix yum errors on CentOS, RHEL or Fedora distributions</a>
</li>
<li class="posts-by-tag-item CentOS Junior nmap nmap version 6.40 Redhat RHEL yum" id="posts-by-tag-item-486">
  <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2014/03/13/how-to-create-a-local-yum-repo-centos-6-x-rhel-6-x/">How to create a local yum repo CentOS 6.x / RHEL 6.x</a>
</li></ul>
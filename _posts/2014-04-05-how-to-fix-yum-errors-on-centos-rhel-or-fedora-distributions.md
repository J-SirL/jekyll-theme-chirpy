---
id: 575
title: How to fix yum errors on CentOS, RHEL or Fedora distributions
date: 2014-04-05T16:03:32+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=575
permalink: /2014/04/05/how-to-fix-yum-errors-on-centos-rhel-or-fedora-distributions/
categories:
  - CentOS
  - Fedora
  - Linux
  - RHEL
tags:
  - CentOS
  - clean
  - Command
  - Fedora
  - metadata
  - RHEL
  - yum
---
Do you have issues when you are trying to update CentOS, Redhat Enterprise Linux or Fedora?

This can be caused by yum metadata that are obsolete or corrupt.

This is how you fix it, first I will show you what the error might look like below:

<pre class="lang:default decode:true" title="yum update error:">pr  5 11:34:46 on hvc0
[root@Host ~]# yum update
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: centos.crazyfrogs.org
 * extras: centos.crazyfrogs.org
 * updates: centos.crazyfrogs.org
http://centos.crazyfrogs.org/6.4/os/x86_64/repodata/repomd.xml: [Errno 14] PYCURL ERROR 22 - "The requested URL returned error: 404 Not Found"
Trying other mirror.
http://centose5.centos.org/centos/6.4/os/x86_64/repodata/repomd.xml: [Errno 14] PYCURL ERROR 22 - "The requested URL returned error: 404 Not Found"
Trying other mirror.
http://centosp3.centos.org/centos/6.4/os/x86_64/repodata/repomd.xml: [Errno 14] PYCURL ERROR 22 - "The requested URL returned error: 404 Not Found"
Trying other mirror.
http://centosp5.centos.org/centos/6.4/os/x86_64/repodata/repomd.xml: [Errno 14] PYCURL ERROR 22 - "The requested URL returned error: 404 Not Found"
Trying other mirror.
http://ftp.cica.es/CentOS/6.4/os/x86_64/repodata/repomd.xml: [Errno 14] PYCURL ERROR 22 - "The requested URL returned error: 404 Not Found"</pre>

As you see in the above screen we have a lot of  &#8220;The requested URL returned error: 404 Not Found&#8221;, To fix this 404 errors you can clean yum metadata by typing the command below:

<pre class="lang:default decode:true" title="command: yum clean metadata">yum clean metadata</pre>

<pre class="lang:default decode:true" title="Outpot of yum clean metadata">[root@host ~]# yum clean metadata
Loaded plugins: fastestmirror
Cleaning repos: base extras updates
10 metadata files removed
3 sqlite files removed
0 metadata files removed</pre>

That worked magic.

You can also use the command:

<pre class="lang:default decode:true" title="Command: yum clean all">yum clean all</pre>

You can check out more information about yum:  
<ul class = "posts-by-tag-list">

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
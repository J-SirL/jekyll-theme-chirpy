---
id: 705
title: install VirtualBox 5 on CentOS 7 using VirtualBox repository
date: 2015-07-11T11:40:05+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=705
permalink: /2015/07/11/install-virtualbox-5-on-centos-7-using-virtualbox-repository/
categories:
  - CentOS
  - Linux
  - RHEL
tags:
  - CentOS
  - provides
  - Repository
  - RHEL
  - VirtualBox
  - yum
---
I just have to create a post about installing VirtualBox 5 on CentOS because I haven&#8217;t seen a good blog post about it at all.

> The repository will update it self to newer versions when they are available, on the bottom of this post you&#8217;ll see the command to check available VirtualBox versions to install.  
> This is an extremely simple procedure so I&#8217;ll skip a long blog post. I&#8217;ll show you how to install VirtualBox in two ways:

## Step 1 download VirtualBox repository directly to the yum repository

<pre class="lang:default decode:true " title="go to repo directory">cd /etc/yum.repos.d/</pre>

Download the repository file directly from virtualbox.org

<pre class="lang:default decode:true" title="Download VirtualBox repository">sudo wget http://download.virtualbox.org/virtualbox/rpm/el/virtualbox.repo</pre>

Update yum before we install VirtualBox 5

<pre class="lang:default decode:true" title="Update yum">sudo yum update -y</pre>

Install VirtualBox 5

<pre class="lang:default decode:true " title="Install VirtualBox but do not use -y because you need to see if recompile kernel was sucessfull">sudo yum install VirtualBox-5.0</pre>

&nbsp;

## Step 2 create the repository list directly using vi editor

first create the file and open it in vi

<pre class="lang:default decode:true " title="Open vi editor and create the virtualbox.repo file">vi /etc/yum.repos.d/virtualbox.repo</pre>

Press I to input text copy and paste the below text:

<pre class="lang:default decode:true " title="Copy  and paste the below text">[virtualbox]
name=Oracle Linux / RHEL / CentOS-$releasever / $basearch - VirtualBox
baseurl=http://download.virtualbox.org/virtualbox/rpm/el/$releasever/$basearch
enabled=1
gpgcheck=1
gpgkey=https://www.virtualbox.org/download/oracle_vbox.asc</pre>

Save and close the file

<pre class="lang:default decode:true " title="Press ESC key then type">:wq</pre>

Update system

<pre class="lang:default decode:true " title="Update system">sudo yum update -y</pre>

Install VirtualBox

<pre class="lang:default decode:true " title="Install VirtualBox">sudo yum install VirtualBox-5.0</pre>

### 

### If you have permission issues or if the kernel didn&#8217;t recompile correctly please run the following command

<pre class="lang:default decode:true  " title="Run this command if you have some issues.">sudo /etc/init.d/vboxdrv setup
</pre>

&nbsp;

### If you are looking for newer or older versions just check for available VitrualBox versions with the below command

<pre class="lang:default decode:true " title="Man this blog post is old I need a newer version so lets check what's availible">sudo yum provides VirtualBox | grep VirtualBox
</pre>

<pre class="lang:default decode:true " title="Example output from the yum provides command">sudo yum provides VirtualBox | grep VirtualBox
VirtualBox-4.3-4.3.18_96516_el7-1.x86_64 : Oracle VM VirtualBox
Filename    : /usr/bin/VirtualBox
VirtualBox-4.3-4.3.20_96996_el7-1.x86_64 : Oracle VM VirtualBox
Filename    : /usr/bin/VirtualBox
VirtualBox-4.3-4.3.22_98236_el7-1.x86_64 : Oracle VM VirtualBox
Filename    : /usr/bin/VirtualBox
VirtualBox-4.3-4.3.24_98716_el7-1.x86_64 : Oracle VM VirtualBox
Filename    : /usr/bin/VirtualBox
VirtualBox-4.3-4.3.26_98988_el7-1.x86_64 : Oracle VM VirtualBox
Filename    : /usr/bin/VirtualBox
VirtualBox-4.3-4.3.28_100309_el7-1.x86_64 : Oracle VM VirtualBox
Filename    : /usr/bin/VirtualBox
VirtualBox-4.3-4.3.30_101610_el7-1.x86_64 : Oracle VM VirtualBox
Filename    : /usr/bin/VirtualBox
VirtualBox-5.0-5.0.0_101573_el7-1.x86_64 : Oracle VM VirtualBox
Filename    : /usr/bin/VirtualBox
</pre>

&nbsp;

&nbsp;
---
id: 699
title: Installation instructions to install Ansible with yum on CentOS 7.x,RHEL 7.x, Fedora 7.x
date: 2015-07-11T09:06:25+02:00
author: Johan Sörell
layout: revision
guid: http://geekcorner.sitedevelopments.net/2015/07/11/698-revision-v1/
permalink: /?p=699
---
So you are staring with Automation, Then I recommend you to install Ansible from the EPEL repository. It super easy so I will not create a huge blog post about this.

Requirements before we install Ansible with yum is of course the EPEL Repository. &#8220;You have Instructions for installing EPEL the easy way in this post: [Install EPEL Repository](http://geekcorner.sitedevelopments.net/2015/07/11/install-the-epel-repository-on-centos-7-x-rhel-7-x-fedora-7-x/)&#8221; The EPEL repository is enabled by default when you follow my instructions so the only thing that I recommend before installing Ansible is to do a system update:

<pre class="lang:default decode:true " title="Udpate dystem before installing Ansible">sudo yum update -y</pre>

Now lets install Ansible

<pre class="lang:default decode:true " title="Install Ansible from the EPEL repository">sudo youm install ansible -y</pre>

&nbsp;

&nbsp;

&nbsp;
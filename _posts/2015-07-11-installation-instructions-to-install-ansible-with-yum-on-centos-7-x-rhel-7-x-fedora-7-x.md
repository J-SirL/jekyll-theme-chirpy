---
id: 698
title: Installation instructions to install Ansible with yum on CentOS 7.x, RHEL 7.x, Fedora 7.x
date: 2015-07-11T09:28:32+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=698
permalink: /2015/07/11/installation-instructions-to-install-ansible-with-yum-on-centos-7-x-rhel-7-x-fedora-7-x/
categories:
  - Ansible
  - CentOS
  - Fedora
  - IT automation
  - Linux
  - RHEL
tags:
  - 7.x
  - CentOS
  - EPEL
  - Fedora
  - IT automation
  - Repository
  - yum
---
So you are staring with Automation, Then I recommend you to install Ansible from the EPEL repository. It super easy so I will not create a huge blog post about this.

Requirements before we install Ansible with yum is of course the EPEL Repository. &#8220;You have Instructions for installing EPEL the easy way in this post: [Install EPEL Repository](http://geekcorner.sitedevelopments.net/2015/07/11/install-the-epel-repository-on-centos-7-x-rhel-7-x-fedora-7-x/)&#8221; The EPEL repository is enabled by default when you follow my instructions so the only thing that I recommend before installing Ansible is to do a system update:

<pre class="lang:default decode:true" title="Update system before installing Ansible">sudo yum update -y</pre>

Now lets install Ansible

<pre class="lang:default decode:true" title="Install Ansible from the EPEL repository">sudo youm install ansible -y</pre>

Lets check the version

<pre class="lang:default decode:true " title="Check Ansible version after the  installation">ansible --version</pre>

<pre class="lang:default decode:true " title="Command ansible --version output example">ansible --version
ansible 1.9.2
  configured module search path = None</pre>

&nbsp;

Now you are ready to start using Ansible.

Enjoy

&nbsp;
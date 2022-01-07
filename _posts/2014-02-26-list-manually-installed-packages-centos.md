---
id: 279
title: List manually installed packages CentOS
date: 2014-02-26T23:18:32+01:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=279
permalink: /2014/02/26/list-manually-installed-packages-centos/
categories:
  - CentOS
tags:
  - CentOS
  - Installed
  - Packages
  - yum
---
Sometime you like to list manually installed packages

just type :

yum list installed | grep -v &#8216;anaconda\|updates&#8217;

and you will get a list of manually installed packages

Read more about yum:<ul class = "posts-by-tag-list">

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
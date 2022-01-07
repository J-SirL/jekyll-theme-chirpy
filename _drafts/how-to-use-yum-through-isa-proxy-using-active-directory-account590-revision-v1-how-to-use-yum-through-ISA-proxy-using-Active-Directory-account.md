---
id: 603
title: how to use yum through ISA proxy using Active Directory account
date: 2014-04-05T18:58:36+02:00
author: Johan Sörell
layout: revision
guid: http://geekcorner.sitedevelopments.net/2014/04/05/590-revision-v1/
permalink: /?p=603
---
If your system is behind a ISA proxy you need to do the following to get yum to work properly.

**Step one: Download the cntlm rpm package**

_For 64 Bit CentOS 6.x_

<pre class="lang:default decode:true" title="Rpm package: cntlm-0.35.1-4.el6.x86_64.rpm">ftp://rpmfind.net/linux/epel/6/x86_64/cntlm-0.35.1-4.el6.x86_64.rpm</pre>

_For 32 Bit CentOS 6.x_

<pre class="lang:default decode:true" title="Rpm Package: cntlm-0.35.1-4.el6.i686.rpm">ftp://rpmfind.net/linux/epel/6/i386/cntlm-0.35.1-4.el6.i686.rpm</pre>

**Step two: Install the rpm package**

_For 64 Bit_

<pre class="lang:default decode:true" title="command: rpm -ivh">rpm -ivh cntlm-0.35.1-4.el6.x86_64.rpm</pre>

_For 32 Bit_

<pre title="Rpm Package: cntlm-0.35.1-4.el6.i686.rpm">rpm -ivh cntlm-0.35.1-4.el6.i686.rpm</pre>

**Step three: Edit /etc/cntlm.conf**

<pre class="lang:default decode:true" title="Edit cntlm.conf">vi /etc/cntlm.conf
Username userxxx   #Domain Account
Domain example.com #Domain Name
Password uiuzdf7/d #Password

Proxy 192.168.1.1:8080 #ISA Proxy</pre>

**Save and quit**

<pre class="lang:default decode:true" title="command to write and quit the vi editor">:wq</pre>

**Step four: Make sure that cntlm now were the confi file is by typing:**

<pre class="lang:default decode:true" title="command cntlm -c filename">cntlm -c /etc/cntlm.conf</pre>

**Info about the switch -c:**

<pre class="lang:default decode:true" title="command swith -c information">cntlm -c 
    Configuration file. Command-line options, if used, override its single options or are added at the top of the list for multi options (tunnels, parent proxies, etc) with the exception of ACLs, which are completely overriden. Use /dev/null to disable any config file.</pre>

**Step five: Edit yum.conf**

<pre class="lang:default decode:true" title="Edit yum.conf">vi /etc/yum.conf</pre>

<pre class="lang:default decode:true" title="Add the line below and save with :wq">proxy=http://127.0.0.1:3128/</pre>

**Save and quit**

<pre class="lang:default decode:true" title="command to write and quit the vi editor">:wq</pre>

**Step six: Edit bash profile**

<pre class="lang:default decode:true" title="Edit .bash_profile">vi .bash_profile</pre>

_ Add the following lines :_

<pre class="lang:default decode:true" title="Add the following lines to .bash_profile">export http_proxy=http://localhost:3128/
export https_proxy=${http_proxy}
export ftp_proxy=${http_proxy}</pre>

**Save and quit**

<pre title="command to write and quit the vi editor">:wq</pre>

**Step seven: log off and login again**

<pre class="lang:default decode:true">logout or exit</pre>

**Step eight: Run the command yum clean all to clear yum**

<pre class="lang:default decode:true" title="command: yum clean all">yum clean all</pre>

**Step nine: install the package you like**

<pre class="lang:default decode:true" title="command: yum install packagename">yum install &lt;package name&gt;</pre>

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
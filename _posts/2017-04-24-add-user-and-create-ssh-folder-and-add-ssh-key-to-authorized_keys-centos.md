---
id: 902
title: 'add user and create  ssh folder and add ssh key to authorized_keys centos'
date: 2017-04-24T23:02:17+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=902
permalink: /2017/04/24/add-user-and-create-ssh-folder-and-add-ssh-key-to-authorized_keys-centos/
categories:
  - CentOS
  - Linux
tags:
  - authorized_keys
  - CentOS
  - Linux
  - RHEL
  - ssh
  - ssh keys
---
First we need to create the user before we create the ssh folder and the file authorized_keys

## Step one user creation

### Add user:

<pre class="lang:default decode:true" title="add user:">sudo useradd theusername
</pre>

### add user to the wheel group  ( -a = append G is group wheel is the group to add the user to! )

<pre class="lang:default decode:true " title="Modify the user and add group wheel">sudo usermod -aG wheel theusername
</pre>

### Set password for user theusername

<pre class="lang:default decode:true" title="Set password for user theusername">sudo passwd theusername</pre>

### Test the sudo for the user theusername

<pre class="lang:default decode:true " title="Test that sudo works">sudo ls -la /root</pre>

## Step two create the .ssh folder and authorized_keys and set permissions

### create .ssh folder

<pre class="lang:default decode:true" title="Create .ssh folder in home directory">mkdir ~/.ssh</pre>

### cretate the file authorized_keys

<pre class="lang:default decode:true" title="create authorized_keys">touch authorized_keys</pre>

### change permissions on ssh folder

<pre class="lang:default decode:true ">chmod 700 ~/.ssh</pre>

### change permission on file authorized_keys

<pre class="lang:default decode:true">chmod 600 ~/.ssh/authorized_keys</pre>

### restore SELinux settings on ~/.ssh

<pre class="lang:default decode:true" title="Restore SELinux">restorecon -Rv ~/.ssh
</pre>

## Step three copy the ssh_key to server

### open ~/.ssh/authorized_keys and add your public key

<pre class="lang:default decode:true ">vi ~/.ssh/authorized_keys</pre>
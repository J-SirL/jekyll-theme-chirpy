---
id: 559
title: Recommended System Swap Space RHEL 6.x / CentOS 6.x / Fedora 6.x
date: 2014-03-25T09:25:09+01:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=559
permalink: /2014/03/25/recommended-system-swap-space-rhel-6-x-centos-6-x-fedora-6-x/
categories:
  - CentOS
  - Fedora
  - Linux
  - RHEL
tags:
  - 6.x
  - CentOS
  - Configuration
  - Fedora
  - Recommended
  - Redhat
  - RHEL
  - Settings
  - System
---
I have had to fix a lot of Linux machines that we have outsourced the hosting on because that the hosting partners Linux specialists can&#8217;t set up the system correctly that&#8217;s why I am going to do a series of recommended environment set-up recommendations here. The recommendations is cut and pasted directly from RedHat&#8217;s recommendations.

This time I will give you a simple table of swap recommendations that you should follow if you are setting up a system with RedHat Enterprise 6.x / CentOS 6.x and Fedora 6.x

<table title="Recommended System Swap Space" summary="Recommended System Swap Space" border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td valign="top">
      <b>Amount of RAM in the system </b>
    </td>
    
    <td valign="top">
      <b>Recommended swap space </b>
    </td>
    
    <td valign="top">
      <b>Recommended swap space if allowing for hibernation </b>
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <b>⩽</b><b>&nbsp;2GB </b>
    </td>
    
    <td valign="top">
      2 times the amount of RAM
    </td>
    
    <td valign="top">
      3 times the amount of RAM
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <b>>&nbsp;2GB – 8GB </b>
    </td>
    
    <td valign="top">
      Equal to the amount of RAM
    </td>
    
    <td valign="top">
      2 times the amount of RAM
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <b>>&nbsp;8GB – 64GB </b>
    </td>
    
    <td valign="top">
      0.5 times the amount of RAM
    </td>
    
    <td valign="top">
      1.5 times the amount of RAM
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <b>>&nbsp;64GB </b>
    </td>
    
    <td valign="top">
      4GB of swap space
    </td>
    
    <td valign="top">
      No extra space needed
    </td>
  </tr>
</table>

<div>
  At the border between each range listed above (for example, a system with 2GB, 8GB, or 64GB of system RAM), discretion can be exercised with regard to chosen swap space and hibernation support. If your system resources allow for it, increasing the swap space may lead to better performance.
</div>

<div>
  Note that distributing swap space over multiple storage devices — particularly on systems with fast drives, controllers and interfaces — also improves swap space performance.
</div>

<div>
  <blockquote>
    <p>
      <strong>Note</strong>
    </p>
    
    <div>
      Swap space size recommendations issued for Red Hat Enterprise Linux 6.0, 6.1, and 6.2 differed from the current recommendations, which were first issued with the release of Red Hat Enterprise Linux 6.3 in June 2012 and did not account for hibernation space. Automatic installations of these earlier versions of Red Hat Enterprise Linux 6 still generate a swap space in line with these superseded recommendations. However, manually selecting a swap space size in line with the newer recommendations issued for Red Hat Enterprise Linux 6.3 is advisable for optimal performance.
    </div>
  </blockquote>
</div>

<div>
  Read more interesting Linux posts:<br /> <ul class = "posts-by-tag-list">
  
  <li class="posts-by-tag-item authorized_keys CentOS Linux RHEL ssh ssh keys" id="posts-by-tag-item-902">
    <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2017/04/24/add-user-and-create-ssh-folder-and-add-ssh-key-to-authorized_keys-centos/">add user and create ssh folder and add ssh key to authorized_keys centos</a>
  </li>
  <li class="posts-by-tag-item CentOS NetworkManager nmtui nmtui-connect nmtui-edit nmtui-hostname RHEL" id="posts-by-tag-item-740">
    <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2015/11/13/nmtui-text-user-interface-for-controlling-networkmanager/">nmtui - Text User Interface for controlling NetworkManager</a>
  </li>
  <li class="posts-by-tag-item CentOS Command Debian Fedora RHEL ss ubu" id="posts-by-tag-item-801">
    <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2015/08/21/net-utils-package-deprecated-ss-and-ip-is-the-replacement-commands-for-rhel-centos-fedora-7/">net-utils package deprecated ss and ip is the replacement commands for RHEL / CentOS / Fedora 7</a>
  </li>
  <li class="posts-by-tag-item 7.x CentOS Dynamic Firewall Manager Fedora firewall firewalld man manual RHEL" id="posts-by-tag-item-756">
    <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2015/08/14/part-1-firewalld-dynamic-firewall-manager-explained-centos-7-rhel-7-fedora/">Part - 1 firewalld - Dynamic Firewall Manager Explained ( CentOS 7, RHEL 7, Fedora)</a>
  </li>
  <li class="posts-by-tag-item CentOS Fedora password RHEL SHA512" id="posts-by-tag-item-753">
    <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2015/08/04/generate-sha512-password-with-centos-7fedora-7-rhel-7/">Generate SHA512 password with CentOS 7,FEDORA 7, RHEL 7</a>
  </li></ul>
</div>
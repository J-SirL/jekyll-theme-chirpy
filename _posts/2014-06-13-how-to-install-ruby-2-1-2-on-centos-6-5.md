---
id: 620
title: How To Install Ruby 2.1.2 On CentOS 6.5
date: 2014-06-13T22:50:39+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=620
permalink: /2014/06/13/how-to-install-ruby-2-1-2-on-centos-6-5/
categories:
  - CentOS
  - Linux
tags:
  - 2.1.2
  - "6.5"
  - CentOS
  - Install
  - Ruby
---
**1. Fist make sure your system is up to date**

    yum update -y 

**2. Then you need to install the development tools needed:**

    yum groupinstall -y development

**3.Download and install rvm with curl**

    curl -L get.rvm.io | bash -s stable

**4.&nbsp; Setup the system environment using rvm shell script:**

    source /etc/profile.d/rvm.sh

**5.&nbsp; Now it&#8217;s time to install ruby I&#8217;m installing ruby 2.1.2**

    rvm get head
    rvm install 2.1.2 

> Note:  
> you can get a error saying:  
> &#8216;Error installing EPEL, it is required for libyaml-devel,  
> either there was an error installing EPEL package,  
> or there was problem checking if libyaml-devel is available / installed.&#8217; Usually you can ignore this and run the rvm install 2.1.2 again.  
> if you are unsure if libyaml-devel is installed you can check this by typing:
> 
>     yum info libyaml-devel

**6. Check ruby version  
** 

    ruby -v

<div>
  Read more interesting ruby posts:<br /> <ul class = "posts-by-tag-list">
  
  <li class="posts-by-tag-item 2.1.2 6.5 CentOS Install Ruby" id="posts-by-tag-item-620">
    <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2014/06/13/how-to-install-ruby-2-1-2-on-centos-6-5/">How To Install Ruby 2.1.2 On CentOS 6.5 </a><br />1. Fist make sure your system is up to date yum update -y 2. Then you need to install the development tools needed: yum groupinstall -y development 3.Download and install rvm with curl curl -L get.rvm.io | bash -s stable &hellip;<p class="read-more">
      <a class="more-link" href="http://geekcorner.sitedevelopments.net/2014/06/13/how-to-install-ruby-2-1-2-on-centos-6-5/"> <span class="screen-reader-text">How To Install Ruby 2.1.2 On CentOS 6.5</span> Read More &raquo;</a>
    </p>
  </li></ul>
</div>
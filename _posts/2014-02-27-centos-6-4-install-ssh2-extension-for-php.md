---
id: 259
title: 'CentOS 6.4 &#8211; Install SSH2 extension for PHP'
date: 2014-02-27T19:20:30+01:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=259
permalink: /2014/02/27/centos-6-4-install-ssh2-extension-for-php/
categories:
  - CentOS
tags:
  - CentOS
  - PHP
  - SSH2
---
Install the necessary packages before you can build/install ssh2 extension

<pre class="lang:default decode:true crayon-selected">yum install gcc php-devel php-pear libssh2 libssh2-devel make</pre>

Install the extension, (hit enter for autodetect when it prompts you)

<pre class="lang:sh decode:true">pecl install -f ssh2</pre>

Once the install is completed, you just have to tell PHP to load the extension when it boots.

<pre class="lang:sh decode:true">touch /etc/php.d/ssh2.ini
echo extension=ssh2.so &gt; /etc/php.d/ssh2.ini</pre>

Restart your webserver and test to see if the changes took effect.

<pre class="lang:sh decode:true">service httpd restart</pre>

You can check it installed with the following command

<pre class="lang:sh decode:true">php -m | grep ssh2</pre>

&nbsp;

&nbsp;
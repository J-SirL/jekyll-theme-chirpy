---
id: 297
title: 'How to: Create a directory with Puppet'
date: 2014-03-01T21:06:52+01:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=297
permalink: /2014/03/01/how-to-create-a-directory-with-puppet/
categories:
  - IT automation
  - Puppet
tags:
  - IT automation
  - Puppet
---
## How to create a directory with puppet

If you are creating a website you need to make sure that the directories are in the remote system before you can push the files in to them this is how you do it.

<pre class="toolbar:2 lang:default decode:true"># make sure that the folder /var/www/myfolder/ 
# is in the new system, including permissions
file { "/var/www/myfolder/":
ensure =&gt; "directory",
owner =&gt; "www-data",
group =&gt; "www-data",
mode =&gt; 644,
}</pre>

&nbsp;
---
id: 895
title: Install Docker-machine on Linux
date: 2017-03-21T01:18:00+01:00
author: Johan Sörell
layout: revision
guid: http://geekcorner.sitedevelopments.net/2017/03/21/890-revision-v1/
permalink: /?p=895
---
Install Docker-machine on Linux

first check latest release of Docker Machine here:

<https://github.com/docker/machine/releases/latest/> 

Replace v0.10.0 with the latest docker-machine version if it has a newer version when you read this.

<pre class="top-set:false bottom-set:false wrap:true lang:default decode:true  " title="Install Docker machine">curl -L https://github.com/docker/machine/releases/download/v0.10.0/docker-machine-`uname -s`-`uname -m` &gt;/tmp/docker-machine 
&&  chmod +x /tmp/docker-machine 
&& sudo cp /tmp/docker-machine /usr/local/bin/docker-machine</pre>

Next I will tell you how to use docker-machine with virtualbox
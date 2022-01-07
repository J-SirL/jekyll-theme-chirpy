---
id: 320
title: 'How to: add ipranges to iptables'
date: 2014-03-02T00:00:27+01:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=320
permalink: /2014/03/02/how-to-add-ipranges-to-iptables/
categories:
  - CentOS
tags:
  - CentOS
  - iptables
---
Howto add ipranges to iptables

Do you need to add an iprange to iptables?

This is how you do it:

<pre class="toolbar:2 nums:false lang:default decode:true">iptables -A INPUT -p tcp --destination-port 9090 -m iprange --src-range 192.168.0.2-192.168.0.200 -j ACCEPT</pre>

Then do not forget to save it:

service iptables save

Then you need to restart the service

service iptables restart
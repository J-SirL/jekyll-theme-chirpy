---
id: 855
title: Setting up a cisco router/switch securely
date: 2015-11-25T20:49:49+01:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=855
permalink: /2015/11/25/setting-up-a-cisco-routerswitch-securely/
categories:
  - Cisco
  - Network
---
<pre class="theme:cisco-router lang:default decode:true  " title="Type enable to get in to the enable mode">Router&gt;
Router&gt;Enable</pre>

<pre class="theme:cisco-router lang:default decode:true" title="Go into config terminal">Router#config t</pre>

<pre class="theme:cisco-router lang:default decode:true" title="Set device name">Router(config)#hostname Router1-1</pre>

<pre class="theme:cisco-router lang:default decode:true ">Router1-1(config)#enable password mePassWord</pre>

<pre class="theme:cisco-router lang:default decode:true">Router1-1(config)#enable secret MeSecretPassword</pre>

<pre class="theme:cisco-router lang:default decode:true" title="Encrypts all plain passwords old and new">Router1-1(config)#service password-encryption</pre>

<pre class="theme:cisco-router lang:default decode:true" title=" ">Router1-1(config)#username meUser Privilege 15 password 0 MeNewPasswordformeUser</pre>

<pre class="theme:cisco-router lang:default decode:true" title="Let's configure message of the day">Router1-1(config)#banner motd # Welcome to Router1-1 #</pre>

<pre class="theme:cisco-router lang:default decode:true" title="And warn user that they must be Autorized or fekk off">Router1-1(config)#banner login $ You have to be authorized to use this device or get the heck out $</pre>

<pre class="theme:cisco-router lang:default decode:true" title="Set domain lookup.">Router1-1(config)#ip domain-lookup</pre>

<pre class="theme:cisco-router lang:default decode:true">Router1-1(config)#ip domain-name sitedevelopments.net</pre>

<pre class="theme:cisco-router lang:default decode:true" title="Name server ip address">Router1-1(config)#ip name-server 192.168.1.12</pre>

<pre class="theme:cisco-router lang:default decode:true " title="Generate rsa keys, Let's shoose 2048">Router1-1(config)#crypto key generate rsa
  The name of this key will be: Router1-1.sitedevelopments.net
  Choose the size of the key modulus in the range of 360 to 2048 for your
  General Purpose Keys. Choosing a key modulud greater than 512 may take a few minutes.
How many bits in the modulus [512}: 2048
% Generating 2048 bit RSA keys, keys will be non-exportable</pre>

<pre class="theme:cisco-router lang:default decode:true " title="Lets configure line connection 0 with password, username, timeout and make sure we do not get our typing on several rows.">Router1-1(config)#line con 0
Router1-1(config-line)#password MePasswd
Router1-1(config-line)#login local
Router1-1(config-line)#exec-timeout 10 0
Router1-1(config-line)#logging synchronous</pre>

<pre class="theme:cisco-router lang:default decode:true" title="Lets configure line vty, with pw and activate user login and ssh">Router1-1(config-line)#line vty 0 15
Router1-1(config-line)#password MePasswd
Router1-1(config-line)#login local
Router1-1(config-line)#exec-timeout 10 0
Router1-1(config-line)#logging synchronous
Router1-1(config-line)#transport input ssh
Router1-1(config-line)#exit
Router1-1(config)#exit
Router1-1#
%SYS-5-CONFIG_I: Configured from console by console</pre>

<pre class="theme:cisco-router lang:default decode:true" title="Lets save the configuration">Router1-1#copy running-config startup-config
Destonation filename [startup-config]?
Building configuration...
[OK]</pre>

<pre class="theme:cisco-router lang:default decode:true " title="Let's see the configuration">Router1-1#show running-config
Your configuration will be shown here</pre>

<pre class="theme:cisco-router lang:default decode:true" title="Show brief interface information">Router1-1#show ip inerface brief
shows you inerfaces</pre>

<pre class="theme:cisco-router lang:default decode:true ">Router1-1#config t
Router1-1(config)#
Router1-1(config)#int F0/0
Router1-1(config-if)#ip address 192.168.1.254 255.255.255.0
Router1-1(config-if)#description connection to LAN
Router1-1(config-if)#no shutdown</pre>

&nbsp;

&nbsp;
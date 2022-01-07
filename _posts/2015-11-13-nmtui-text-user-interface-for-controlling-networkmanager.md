---
id: 740
title: 'nmtui &#8211; Text User Interface for controlling NetworkManager'
date: 2015-11-13T18:19:57+01:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=740
permalink: /2015/11/13/nmtui-text-user-interface-for-controlling-networkmanager/
image: http://media.sitedevelopments.net/2015/07/nmtui.png
categories:
  - CentOS
  - Linux
  - RHEL
tags:
  - CentOS
  - NetworkManager
  - nmtui
  - nmtui-connect
  - nmtui-edit
  - nmtui-hostname
  - RHEL
---
This is a guide to nmtui for CentOS 7 (RHEL 7)

nmtui  stands for: Network Manager Text User Interface and it is used for controlling NetworkManager

These are the commands:  
**nmtui** [ <span style="text-decoration: underline;">edit</span> | <span style="text-decoration: underline;">connect</span> | <span style="text-decoration: underline;">hostname</span> ] [ &#8230; ]

When you type the command nmtui you will be asked what you want to do: Edit A connection, Activate a connection or Set system name

<pre class="lang:default decode:true" title="NetWorkTextUserInterface">nmtui</pre><figure id="attachment_748" aria-describedby="caption-attachment-748" style="width: 327px" class="wp-caption alignnone">

[<img loading="lazy" class="wp-image-748 size-full" src="http://media.sitedevelopments.net/2015/07/nmtui.png" alt="nmtui menu" width="327" height="327" data-wp-pid="748" srcset="http://media.sitedevelopments.net/2015/07/nmtui.png 327w, http://media.sitedevelopments.net/2015/07/nmtui-150x150.png 150w, http://media.sitedevelopments.net/2015/07/nmtui-300x300.png 300w, http://media.sitedevelopments.net/2015/07/nmtui-100x100.png 100w, http://media.sitedevelopments.net/2015/07/nmtui-200x200.png 200w" sizes="(max-width: 327px) 100vw, 327px" />](http://media.sitedevelopments.net/2015/07/nmtui.png)<figcaption id="caption-attachment-748" class="wp-caption-text">nmtui menu</figcaption></figure> 

**nmtui-edit** [ <span style="text-decoration: underline;">connection-id</span> | <span style="text-decoration: underline;">connection-name</span> ]

**nmtui-connect** [ <span style="text-decoration: underline;">connection-name</span> | <span style="text-decoration: underline;">connection-uuid</span> | <span style="text-decoration: underline;">device-name</span> | <span style="text-decoration: underline;">Wi-Fi-SSID</span> ]

**nmtui-hostname**

DESCRIPTION  
nmtui is a curses‐based TUI application for interacting with NetworkManager.

When starting nmtui, the user is prompted to choose the activity to perform unless it was specified as the first argument.

The supported activities are:

— **edit**: show a connection editor that supports adding, modifying, viewing and deleting connections. It provides similar functionality as nm-connection-editor.

— **connect**: show a list of available connections, with the option to activate or deactivate them. It provides similar functionality as nm-applet.

— **hostname**: set the system hostname.

Corresponding to above activities, nmtui also comes with binaries named **nmtui-edit**, **nmtui-connect**, and **nmtui-hostname** to skip the selection of the activities.

SEE ALSO man pages:

<span class="lang:default decode:true crayon-inline">man 8 NetworkManager</span>

<span class="lang:default decode:true crayon-inline">man nmcli</span>

<span class="lang:default decode:true crayon-inline ">man nm-applet</span>

<span class="lang:default decode:true crayon-inline ">man nm-connection-editor</span>

&nbsp;
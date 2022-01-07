---
id: 254
title: 'Windows 2012: PowerShell'
date: 2013-07-18T20:14:24+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=254
permalink: /2013/07/18/windows-2012-powershell/
categories:
  - PowerShell
  - Windows
  - Windows 2012
tags:
  - PowerShell
  - Windows 2012
---
This is how you change DVD drive letter in PowerShell.

<pre class="lang:ps decode:true">(gwmi Win32_cdromdrive).drive | %{$a = mountvol $_ /l;mountvol $_ /d;$a = $a.Trim();mountvol z: $a}</pre>

&nbsp;
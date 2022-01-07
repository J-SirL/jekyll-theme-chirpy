---
id: 831
title: 'Xenserver &#8211; FIX VDI not available'
date: 2015-11-20T14:51:40+01:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=831
permalink: /2015/11/20/xenserver-fix-vdi-not-available/
categories:
  - XenServer
tags:
  - VDI
  - XenServer
---
# FIX VDI not available

Run the following command on each host to verify that the VM is shutdown and is not running on any of the hosts:  
<span class="lang:default decode:true crayon-inline ">list_domains | grep <VM UUID></span>  
For example <span class="lang:default decode:true crayon-inline">[root@localhost log]# list_domains | grep c4615dc5-a7ff-bf10-e675-49e64a749fb5</span>  
If the response indicates any running VM, shut down the machine and reset the VDI, to allow the VM to start without error.

To get the , run the following command and then the script.  
<span class="lang:default decode:true crayon-inline"># xe vm-disk-list uuid=<VM_UUID></span>  
Note: You will get two UUIDs of the following format-  
a.VBD_UUID  
b.VDI_UUID 

Ensure to use **VDI_UUID** and not VBD_UUID.

For hosts running post XenServer 6.1 with update XS61E015, the resetvdis.py script has been updated to allow a single VDI to be reset without having to stop all VMs running on the same SR.  
Reset the VDI using the following resetvdis.py command syntax:  
<span class="lang:default decode:true crayon-inline">/opt/xensource/sm/resetvdis.py single <VM_UUID></span>

Use the VDI UUID from the error message or refer to the previous step.

To reset all VDIs together in a SR, use the following command:

<pre class="lang:default decode:true " title="Warning do not use this on a system with VM's running">#/opt/xensource/sm/resetvdis.py all &lt;HOST_UUID&gt;  &lt;SR_UUID&gt;</pre>

> WARNING! Calling with &#8216;all&#8217; on an attached SR, or using &#8211;force may cause DATA CORRUPTION if the VDI is still attached somewhere.  
> Always manually double-check that the VDI is not in use before running this script.

To manually check if a VDI is still attached, use the following command on each host:  
<span class="lang:default decode:true crayon-inline ">tap-ctl list | grep&nbsp;<VM_UUID> </span>

> For hosts running XenServer versions prior to XenServer 6.1 with update XS61E015, the resetvdis.py script can only be run on the entire SR. All VMs on that SR have to be shutdown.
> 
> Information taken from
> 
> <div class="articleNumber notranslate">
>   <a href="http://support.citrix.com/article/CTX138234?_ga=1.47054435.559671654.1433764107">CTX138234</a>
> </div>
> 
> <div class="articleNumber notranslate">
>
> </div>
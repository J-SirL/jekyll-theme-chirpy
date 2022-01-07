---
id: 233
title: 'XenServer 6.2: Installing update using the xe Command Line Interface'
date: 2013-07-14T20:02:55+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=233
permalink: /2013/07/14/xenserver-6-2-installing-update-using-the-xe-command-line-interface/
categories:
  - Virtualization
  - XenServer
tags:
  - "6.2"
  - CLI
  - Comand Line Interface
  - Update
  - xe
  - XenServer
---
### Installing the update using the xe Command Line Interface

  1. Download the update file to a known location.
  2. Extract the xsupdate file from the zip.  
    In _this example I am patching the xenserver with the_ **XS62E002** update
  3. Upload the xsupdate file to the Pool Master by entering the following commands:  
    (Where <tt>hostname</tt> is the Pool Master&#8217;s IP address or DNS name.)</p> <pre class="theme:terminal nums:false nums-toggle:false lang:default decode:true">xe patch-upload -s &lt;hostname&gt; -u root -pw &lt;password&gt; file-name=&lt;path_to_update_file&gt;\XS62E002.xsupdate</pre>
    
    XenServer assigns the update file a UUID which this command prints. Note the UUID.
    
    > <tt>59128f15-92cd-4dd9-8fbe-a0115d1b07a2</tt>

  1. Apply the hotfix to all hosts in the pool, specifying the UUID of the hotfix: <pre class="theme:terminal nums:false nums-toggle:false lang:default decode:true ">xe -s &lt;hostname&gt; -u root -pw &lt;password&gt; patch-pool-apply uuid=59128f15-92cd-4dd9-8fbe-a0115d1b07a2</pre>
    
    &nbsp;</li> 
    
      * Verify that the update was applied by using the **patch-list** command. <pre class="theme:terminal nums:false nums-toggle:false lang:default decode:true ">xe patch-list -s &lt;hostname&gt; -u root -pw &lt;password&gt; name-label=XS62E002</pre>
        
        If the update has been successful, the <tt>hosts</tt> field will contain the UUIDs of the hosts this patch was successfully applied to. This should be a complete list of all hosts in the pool.</li> 
        
          * To verify in XenCenter that the update has been applied correctly, select the Pool, and then click the **General** tab. This displays the Pool properties. In the **Updates** section, ensure that the update is listed as **Fully Applied**.
          * The hotfix is applied to all hosts in the pool, but it will not take effect until each host has been rebooted. For each host, migrate the VMs that you wish to keep running, and shutdown the remaining VMs before rebooting the host.</ol>
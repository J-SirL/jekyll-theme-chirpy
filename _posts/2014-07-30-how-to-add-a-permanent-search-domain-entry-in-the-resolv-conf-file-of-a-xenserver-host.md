---
id: 660
title: How to Add a Permanent Search Domain Entry in the Resolv.conf File of a XenServer Host
date: 2014-07-30T18:42:59+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=660
permalink: /2014/07/30/how-to-add-a-permanent-search-domain-entry-in-the-resolv-conf-file-of-a-xenserver-host/
categories:
  - CentOS
  - Linux
  - RHEL
  - XenServer
tags:
  - resolve.conf
  - Search Domain
  - XenServer
---
This post describes how to add a permanent search domain entry in the resolv.cof of a XenServer Host. Because if you try to manually edit resolv.conf to add search domains the entries are not persistent after the XenServer Host reboot.

## Instructions {#Instructions.sectionTitle}

<div id="sectionContent" class="sectionContent">
  <div class="parsys sectionitempar">
    <div class="htmlRender section">
      <p>
        The following are the requirements:
      </p>
      
      <ul>
        <li>
          XenServer 5.0 and later
        </li>
        <li>
          Access to the command line interface of the XenServer host
        </li>
        <li>
          The Network Interface Cards (NICs) on the XenServer host must be configured with a static IP address
        </li>
      </ul>
      
      <p>
        Complete the following procedure:
      </p>
      
      <ol>
        <li>
          To identify the management NIC on a given host run, run the following command: <pre class="lang:default decode:true">xe pif-list host-name-label= management=true</pre>
        </li>
        
        <li>
          To add the static search domain entry to the resolv.conf: <pre class="lang:default decode:true">xe pif-param-set uuid= other-config:domain=searchdomain.net</pre>
        </li>
        
        <li>
          Reboot the XenServer Host.
        </li>
        <li>
          The <strong>cat /etc/resolv.conf</strong> displays the search domain entry.
        </li>
      </ol>
      
      <p>
        <strong>Note</strong>: Multiple search domain entries can be entered separated by commas:
      </p>
      
      <pre class="lang:default decode:true ">xe pif-param-set uuid= other-config:domain=searchdomain.net,searchdomain2.net</pre>
      
      <p>
        &nbsp;
      </p>
      
      <h2 id="ApplicableProducts" class="sectionTitle">
        Applicable Products
      </h2>
      
      <div id="sectionContent" class="sectionContent">
        <div class="parsys sectionitempar">
          <div class="citrixproductslist section">
            <ul class="notranslate">
              <li>
                <a href="http://support.citrix.com/search?prod=XenServer&pver=XenServer%206.2.0">XenServer 6.2.0</a>
              </li>
              <li>
                <a href="http://support.citrix.com/search?prod=XenServer&pver=XenServer%206.1.0">XenServer 6.1.0</a>
              </li>
              <li>
                <a href="http://support.citrix.com/search?prod=XenServer&pver=XenServer%206.0">XenServer 6.0</a>
              </li>
            </ul>
          </div>
        </div>
      </div>
      
      <p>
        Sources:
      </p>
      
      <p>
        <a title="Citrix support article # CTX118840" href="http://support.citrix.com/article/CTX118840">CTX118840</a>
      </p>
    </div>
  </div>
</div>
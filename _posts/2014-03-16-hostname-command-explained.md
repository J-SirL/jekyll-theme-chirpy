---
id: 400
title: hostname command explained
date: 2014-03-16T13:39:33+01:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=400
permalink: /2014/03/16/hostname-command-explained/
categories:
  - CentOS
  - Linux
  - RHEL
tags:
  - CentOS
  - Command
  - explained
  - Junior
  - Linux
  - Redhat
  - RHEL
---
## Command: hostname explained

I have seen a lot of people telling people to use the command hostname to get FQDN but almost none that have explained to junior people what the command actually does more than hostname -f. So I decided to start explaining a lot of the Linux commands that are used daily if not weekly as a Linux System Administrator. So enjoy the first of many commands I will explain in detail here at geekcorner.sitedevelopments.net.

This command can read or set the hostname or the NIS domain name. You can  
also read the DNS domain or the FQDN (fully qualified domain name).  
Unless you are using bind or NIS for host lookups you can change the  
FQDN (Fully Qualified Domain Name) and the DNS domain name (which is  
part of the FQDN) in the /etc/hosts file.

## Usage:

-i, &#8211;ip-address      addresses for the hostname  
-I, &#8211;all-ip-addresses all addresses for the host

Check ip Address for the hostname

<pre class="lang:default decode:true" title="The command: hostname -i show's the ip adress for the hostname">hostname i</pre>

<pre class="lang:default decode:true" title="Command output: hostname -i">hostname -i
127.0.0.1</pre>

Check all IP Addresses for the hostname

-I, &#8211;all-ip-addresses all addresses for the host

<pre class="lang:default decode:true" title="The command: hostname -I show's all IP addresses for the host">hostname -I</pre>

As you see below the command do not show the loopback IP address only sharp ip adresses.,

<pre class="lang:default decode:true" title="Command out put for: hostname -I">hostname -I
10.101.1.152</pre>

Check the aliases for hostname

-a, &#8211;alias           alias names

hostname -a

<pre class="lang:default decode:true" title="Command output: hostname -a show hostname aliases">$ hostname -a
sesstl168 localhost.localdomain localhost</pre>

Check the short host name

-s, –short           short host name

hostname -s

<pre class="lang:default decode:true" title="Command: hostname -s shows short host name">hostname -s
sesstl168</pre>

Check the Fully Qualified Domain Name (FQDN)

-f, &#8211;fqdn, &#8211;long    long host name (FQDN)

hostname -f

<pre class="lang:default decode:true" title="Command: hostname -f shows the long host name (FQDN)">hostname -f
sesstl168.sitedevelopments.local</pre>

Check all FDQDN

-A, &#8211;all-fqdns        all long host names (FQDNs)

hostname -A

<pre class="lang:default decode:true" title="Command output: hostname -A">hostname -A
sesstl168.sitedevelopments.net</pre>

As you see here the command hostname -A will only show the FQDN that have a real IP address it will not show loopback FQDN

### Set hostname from a file

<pre class="toolbar:1 nums:false nums-toggle:false lang:default decode:true" title="Note: hostname changes are not static with this metod.">hostname [-v] {hostname|-F file}</pre>

Command Explanation:

hostname [-v]     display hostname  
-F, &#8211;file            read hostname or NIS domainname from given file

In the example below I load the hostname **newhostname** from the file **myhostname** that are located in my home folder.

As you see the file contains only the hostname

<pre class="lang:default decode:true" title="The example file myhostname">cat /home/johan/myhostname
newhostname</pre>

<pre class="toolbar:1 nums:false lang:default decode:true" title="The command: to set hostname tmporary from a file">sudo hostname -v hostname -F /home/johan/mydomainname</pre>

<pre class="toolbar:1 toolbar-delay:false nums:false nums-toggle:false lang:default decode:true" title="Output of command: sudo hostname -v hostname -F /home/johan/myhostname">[sudo] password for johan: 
&gt;&gt; newhostname
Setting hostname to `newhostname'</pre>

To check the result of the command we just typed type: **hostname -v** it will display the name.

Below is the output of **hostname -v **after I ran the command above.

<pre class="toolbar:1 nums:false lang:default decode:true" title="The command: hostname -v displays hostname">$ hostname -v
gethostname()=`newhostname'
newhostname</pre>

hostname \[-v\] \[-d|-f|-s|-a|-i|-y|-A|-I\]  display formatted name

hostname [-v]                         display hostname

hostname -V|&#8211;version|-h|&#8211;help       print info and exit

<pre class="lang:default decode:true" title="hostname -V|--version|-h|--help  ">hostname -Vh</pre>

<pre class="lang:default decode:true" title="Output Example:  hostname -Vh">[c-johsor@sesstl168 ~]$ hostname -Vh
net-tools 1.60
hostname 1.100 (2001-04-14)
[c-johsor@sesstl168 ~]$</pre>

Finaly you can use hostname -h to get help

<pre class="lang:default decode:true" title="hostname -h help output">hostname -h
Usage: hostname [-v] {hostname|-F file}      set hostname (from file)
       domainname [-v] {nisdomain|-F file}   set NIS domainname (from file)
       hostname [-v] [-d|-f|-s|-a|-i|-y|-A|-I]  display formatted name
       hostname [-v]                         display hostname

       hostname -V|--version|-h|--help       print info and exit

    dnsdomainname=hostname -d, {yp,nis,}domainname=hostname -y

    -s, --short           short host name
    -a, --alias           alias names
    -i, --ip-address      addresses for the hostname
    -I, --all-ip-addresses all addresses for the host
    -f, --fqdn, --long    long host name (FQDN)
    -A, --all-fqdns        all long host names (FQDNs)
    -d, --domain          DNS domain name
    -y, --yp, --nis       NIS/YP domainname
    -F, --file            read hostname or NIS domainname from given file

   This command can read or set the hostname or the NIS domainname. You can
   also read the DNS domain or the FQDN (fully qualified domain name).
   Unless you are using bind or NIS for host lookups you can change the
   FQDN (Fully Qualified Domain Name) and the DNS domain name (which is
   part of the FQDN) in the /etc/hosts file.</pre>

That&#8217;s all folk.

Do you like to check out other commands that I&#8217;m explaining check out the below post:<ul class = "posts-by-tag-list">

<li class="posts-by-tag-item CentOS Command Debian Fedora RHEL ss ubu" id="posts-by-tag-item-801">
  <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2015/08/21/net-utils-package-deprecated-ss-and-ip-is-the-replacement-commands-for-rhel-centos-fedora-7/">net-utils package deprecated ss and ip is the replacement commands for RHEL / CentOS / Fedora 7</a>
</li>
<li class="posts-by-tag-item CentOS cntlm Command ISA Linux proxy Redhat RHEL yum" id="posts-by-tag-item-590">
  <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2014/04/05/how-to-use-yum-through-isa-proxy-using-active-directory-account/">how to use yum through ISA proxy using Active Directory account</a>
</li>
<li class="posts-by-tag-item CentOS clean Command Fedora metadata RHEL yum" id="posts-by-tag-item-575">
  <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2014/04/05/how-to-fix-yum-errors-on-centos-rhel-or-fedora-distributions/">How to fix yum errors on CentOS, RHEL or Fedora distributions</a>
</li>
<li class="posts-by-tag-item CentOS Command explained Junior Linux Redhat RHEL" id="posts-by-tag-item-400">
  <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2014/03/16/hostname-command-explained/">hostname command explained</a>
</li>
<li class="posts-by-tag-item CentOS Command explained Junior network nmap Redhat RHEL scan" id="posts-by-tag-item-444">
  <a class = "posts-by-tag-item-title" href="http://geekcorner.sitedevelopments.net/2014/03/12/how-to-use-nmap-to-scan-the-network-for-live-hosts-centosrhel/">How to use nmap to scan the network for live hosts CentOS/RHEL</a>
</li></ul>
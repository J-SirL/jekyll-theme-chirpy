---
id: 801
title: 'net-utils package deprecated ss and ip is the replacement commands  for RHEL / CentOS / Fedora 7'
date: 2015-08-21T23:34:53+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=801
permalink: /2015/08/21/net-utils-package-deprecated-ss-and-ip-is-the-replacement-commands-for-rhel-centos-fedora-7/
categories:
  - CentOS
  - Fedora
  - Linux
  - RHEL
  - Ubuntu
tags:
  - CentOS
  - Command
  - Debian
  - Fedora
  - RHEL
  - ss
  - ubu
---
> The ifconfig and netstat utilities has been marked as deprecated in the man pages for CentOS 5 and 6 for nearly a decade.  Redhat made the decision to no longer install the net-utils package by default in CentOS 7. The replacement utilities are ss and ip. If you really need ifconfig and netstat back then you can yum install net-utils. Source: [CentOS Wiki FAQ](http://wiki.centos.org/FAQ/CentOS7#head-e6388c11ed84c9b8a643a69d85a2ae426aaa9f0b)

### Below is the Man page for the SS command

**NAME**  
_ss &#8211; another utility to investigate sockets_

**SYNOPSIS**  
ss \[options\] \[ FILTER \]

**DESCRIPTION**  
ss is used to dump socket statistics. It allows showing information similar to netstat.  It can display more TCP and state informations than other tools.

**OPTIONS**  
When no option is used ss displays a list of open non-listening TCP sockets that have established connection.

**-h, &#8211;help**  
Show summary of options.

**-V, &#8211;version**  
Output version information.

**-n, &#8211;numeric**  
Do not try to resolve service names.

**-r, &#8211;resolve**  
Try to resolve numeric address/ports.

**-a, &#8211;all**  
Display both listening and non-listening (for TCP this means established connections) sockets.

**-l, &#8211;listening**  
Display only listening sockets (these are omitted by default).

**-o, &#8211;options**  
Show timer information.

**-e, &#8211;extended**  
Show detailed socket information

**-m, &#8211;memory**  
Show socket memory usage.

**-p, &#8211;processes**  
Show process using socket.

**-i, &#8211;info**  
Show internal TCP information.

**-s, &#8211;summary**  
Print summary statistics. This option does not parse socket lists obtaining summary from various sources. It is useful when amount of sockets is so huge that parsing /proc/net/tcp is painful.

**-b, &#8211;bpf**  
Show socket BPF filters (only administrators are allowed to get these information).

**-4, &#8211;ipv4**  
Display only IP version 4 sockets (alias for -f inet).

**-6, &#8211;ipv6**  
Display only IP version 6 sockets (alias for -f inet6).

**-0, &#8211;packet**  
Display PACKET sockets (alias for -f link).

**-t, &#8211;tcp**  
Display TCP sockets.

**-u, &#8211;udp**  
Display UDP sockets.

**-d, &#8211;dccp**  
Display DCCP sockets.

**-w, &#8211;raw**  
Display RAW sockets.

**-x, &#8211;unix**  
Display Unix domain sockets (alias for -f unix).

**-f FAMILY, &#8211;family=FAMILY**  
Display sockets of type FAMILY.  Currently the following families are supported: unix, inet, inet6, link, netlink.

**-A QUERY, &#8211;query=QUERY, &#8211;socket=QUERY**  
List  of  socket  tables  to  dump,  separated  by  commas.  The  following  identifiers  are understood: all, inet, tcp, udp, raw, unix, packet, netlink, unix\_dgram, unix\_stream, packet_raw,  
packet_dgram.

**-D FILE, &#8211;diag=FILE**  
Do not display anything, just dump raw information about TCP sockets to FILE after applying filters. If FILE is &#8211; stdout is used.

**-F FILE, &#8211;filter=FILE**  
Read filter information from FILE.  Each line of FILE is interpreted like single command line option. If FILE is &#8211; stdin is used.

**FILTER := \[ state TCP-STATE \] \[ EXPRESSION \]**  
Please take a look at the official documentation (Debian package iproute-doc) for details regarding filters.

**USAGE EXAMPLES**

<span class="lang:default decode:true  crayon-inline ">ss -t -a</span>  
Display all TCP sockets.

<span class="lang:default decode:true  crayon-inline ">ss -u -a</span>  
Display all UDP sockets.

<span class="lang:default decode:true  crayon-inline ">ss -o state established &#8216;( dport = :ssh or sport = :ssh )&#8217;</span>  
Display all established ssh connections.

<span class="lang:default decode:true  crayon-inline ">ss -x src /tmp/.X11-unix/*</span>  
Find all local processes connected to X server.

<span class="lang:default decode:true  crayon-inline ">ss -o state fin-wait-1 &#8216;( sport = :http or sport = :https )&#8217; dst 193.233.7/24</span>  
List all the tcp sockets in state FIN-WAIT-1 for our apache to network 193.233.7/24 and look at their timers.

**SEE ALSO**  
<span class="lang:default decode:true  crayon-inline ">man ip</span> , /usr/share/doc/iproute-doc-3.10.0/ss.ps (package iproute-doc)

**AUTHOR**  
ss was written by _Alexey Kuznetosv,_

This manual page was written by _Michael Prokop _ for the Debian project (but may be used by others).
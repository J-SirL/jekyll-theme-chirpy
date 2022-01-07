---
id: 663
title: Howto install GlusterFS 3.5.1 on CentOS 6.5
date: 2014-07-03T23:21:42+02:00
author: Johan Sörell
layout: post
guid: http://geekcorner.sitedevelopments.net/?p=663
permalink: /2014/07/03/howto-install-glusterfs-3-5-1-on-centos-6-5/
categories:
  - CentOS
  - Linux
tags:
  - CentOS
  - GlusterFS
---
## **This is a guide to install GlusterFS 3.5.1 on CentOS**

Requirements:

  1. **CentOS 6.x &#8220;I&#8217;m doing this on CentOS 6.5&#8221;**
  2. **Configured Network**
  3. **wget installed on the OS**

**Resourses:**

  * [GlusterFS Documentation](http://www.gluster.org/community/documentation/index.php/Main_Page "GlusterFS Documentation")

**Let&#8217;s start the installation**

**1. Go to /etc/yum.repolist.d**

<pre class="lang:default decode:true">cd /etc/yum.repolist.d</pre>

**2. Download the repo**

<pre class="lang:default decode:true">wget http://download.gluster.org/pub/gluster/glusterfs/3.5/3.5.1/EPEL.repo/glusterfs-epel.repo</pre>

**3. check that the glusterfs repo are installed correctly**

<pre class="lang:default decode:true">yum repolist</pre>

<pre class="lang:default decode:true" title="output"># yum repolist
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: ftp.availo.se
 * extras: ftp.availo.se
 * updates: ftp.availo.se
repo id               repo name                                           status
base                  CentOS-6 - Base                                     6,367
extras                CentOS-6 - Extras                                      14
glusterfs-epel        GlusterFS is a clustered file-system capable of sca    13
glusterfs-noarch-epel GlusterFS is a clustered file-system capable of sca     1
updates               CentOS-6 - Updates                                  1,104
repolist: 7,499
[root@localhost yum.repos.d]#</pre>

**4.  Install glusterfs-server**

<pre class="lang:default decode:true" title="Install glusterFS Server and Client">yum isntall glusterfs-server</pre>

<pre class="lang:default decode:true" title="Output:"># yum install glusterfs-server
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: ftp.availo.se
 * extras: ftp.availo.se
 * updates: ftp.availo.se
Setting up Install Process
Resolving Dependencies
--&gt; Running transaction check
---&gt; Package glusterfs-server.x86_64 0:3.5.1-1.el6 will be installed
--&gt; Processing Dependency: glusterfs-libs = 3.5.1-1.el6 for package: glusterfs-server-3.5.1-1.el6.x86_64
--&gt; Processing Dependency: glusterfs-fuse = 3.5.1-1.el6 for package: glusterfs-server-3.5.1-1.el6.x86_64
--&gt; Processing Dependency: glusterfs-cli = 3.5.1-1.el6 for package: glusterfs-server-3.5.1-1.el6.x86_64
--&gt; Processing Dependency: glusterfs = 3.5.1-1.el6 for package: glusterfs-server-3.5.1-1.el6.x86_64
--&gt; Processing Dependency: rpcbind for package: glusterfs-server-3.5.1-1.el6.x86_64
--&gt; Processing Dependency: libglusterfs.so.0()(64bit) for package: glusterfs-server-3.5.1-1.el6.x86_64
--&gt; Processing Dependency: libgfxdr.so.0()(64bit) for package: glusterfs-server-3.5.1-1.el6.x86_64
--&gt; Processing Dependency: libgfrpc.so.0()(64bit) for package: glusterfs-server-3.5.1-1.el6.x86_64
--&gt; Processing Dependency: libgfapi.so.0()(64bit) for package: glusterfs-server-3.5.1-1.el6.x86_64
--&gt; Running transaction check
---&gt; Package glusterfs.x86_64 0:3.5.1-1.el6 will be installed
---&gt; Package glusterfs-api.x86_64 0:3.5.1-1.el6 will be installed
---&gt; Package glusterfs-cli.x86_64 0:3.5.1-1.el6 will be installed
---&gt; Package glusterfs-fuse.x86_64 0:3.5.1-1.el6 will be installed
---&gt; Package glusterfs-libs.x86_64 0:3.5.1-1.el6 will be installed
---&gt; Package rpcbind.x86_64 0:0.2.0-11.el6 will be installed
--&gt; Processing Dependency: libgssglue for package: rpcbind-0.2.0-11.el6.x86_64
--&gt; Processing Dependency: libtirpc.so.1()(64bit) for package: rpcbind-0.2.0-11.el6.x86_64
--&gt; Processing Dependency: libgssglue.so.1()(64bit) for package: rpcbind-0.2.0-11.el6.x86_64
--&gt; Running transaction check
---&gt; Package libgssglue.x86_64 0:0.1-11.el6 will be installed
---&gt; Package libtirpc.x86_64 0:0.2.1-6.el6_5.2 will be installed
--&gt; Finished Dependency Resolution

Dependencies Resolved

==================================================================================================================================================================================================
 Package                                           Arch                                    Version                                          Repository                                       Size
==================================================================================================================================================================================================
Installing:
 glusterfs-server                                  x86_64                                  3.5.1-1.el6                                      glusterfs-epel                                  562 k
Installing for dependencies:
 glusterfs                                         x86_64                                  3.5.1-1.el6                                      glusterfs-epel                                  1.2 M
 glusterfs-api                                     x86_64                                  3.5.1-1.el6                                      glusterfs-epel                                   69 k
 glusterfs-cli                                     x86_64                                  3.5.1-1.el6                                      glusterfs-epel                                  122 k
 glusterfs-fuse                                    x86_64                                  3.5.1-1.el6                                      glusterfs-epel                                   92 k
 glusterfs-libs                                    x86_64                                  3.5.1-1.el6                                      glusterfs-epel                                  249 k
 libgssglue                                        x86_64                                  0.1-11.el6                                       base                                             23 k
 libtirpc                                          x86_64                                  0.2.1-6.el6_5.2                                  updates                                          79 k
 rpcbind                                           x86_64                                  0.2.0-11.el6                                     base                                             51 k

Transaction Summary
==================================================================================================================================================================================================
Install       9 Package(s)

Total download size: 2.4 M
Installed size: 7.8 M
Is this ok [y/N]:
</pre>

**Press Y to continue**

<pre class="lang:default decode:true" title="Output:">Downloading Packages:
(1/9): glusterfs-3.5.1-1.el6.x86_64.rpm                                                                                                                                    | 1.2 MB     00:01
(2/9): glusterfs-api-3.5.1-1.el6.x86_64.rpm                                                                                                                                |  69 kB     00:00
(3/9): glusterfs-cli-3.5.1-1.el6.x86_64.rpm                                                                                                                                | 122 kB     00:00
(4/9): glusterfs-fuse-3.5.1-1.el6.x86_64.rpm                                                                                                                               |  92 kB     00:00
(5/9): glusterfs-libs-3.5.1-1.el6.x86_64.rpm                                                                                                                               | 249 kB     00:00
(6/9): glusterfs-server-3.5.1-1.el6.x86_64.rpm                                                                                                                             | 562 kB     00:00
(7/9): libgssglue-0.1-11.el6.x86_64.rpm                                                                                                                                    |  23 kB     00:00
(8/9): libtirpc-0.2.1-6.el6_5.2.x86_64.rpm                                                                                                                                 |  79 kB     00:00
(9/9): rpcbind-0.2.0-11.el6.x86_64.rpm                                                                                                                                     |  51 kB     00:00
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                                             459 kB/s | 2.4 MB     00:05
warning: rpmts_HdrFromFdno: Header V4 RSA/SHA1 Signature, key ID 4ab22bb3: NOKEY
Retrieving key from http://download.gluster.org/pub/gluster/glusterfs/LATEST/EPEL.repo/pub.key
Importing GPG key 0x4AB22BB3:
 Userid: "Gluster Packager &lt;glusterpackager@download.gluster.org&gt;"
 From  : http://download.gluster.org/pub/gluster/glusterfs/LATEST/EPEL.repo/pub.key
Is this ok [y/N]:
</pre>

**Check that the key is ok if yes the continue with y**

<pre class="lang:default decode:true" title="Output:">Is this ok [y/N]: y
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing : glusterfs-libs-3.5.1-1.el6.x86_64                                                                                                                                              1/9
  Installing : glusterfs-3.5.1-1.el6.x86_64                                                                                                                                                   2/9
  Installing : libgssglue-0.1-11.el6.x86_64                                                                                                                                                   3/9
  Installing : libtirpc-0.2.1-6.el6_5.2.x86_64                                                                                                                                                4/9
  Installing : rpcbind-0.2.0-11.el6.x86_64                                                                                                                                                    5/9
  Installing : glusterfs-api-3.5.1-1.el6.x86_64                                                                                                                                               6/9
  Installing : glusterfs-fuse-3.5.1-1.el6.x86_64                                                                                                                                              7/9
  Installing : glusterfs-cli-3.5.1-1.el6.x86_64                                                                                                                                               8/9
  Installing : glusterfs-server-3.5.1-1.el6.x86_64                                                                                                                                            9/9
  Verifying  : glusterfs-cli-3.5.1-1.el6.x86_64                                                                                                                                               1/9
  Verifying  : glusterfs-api-3.5.1-1.el6.x86_64                                                                                                                                               2/9
  Verifying  : rpcbind-0.2.0-11.el6.x86_64                                                                                                                                                    3/9
  Verifying  : glusterfs-fuse-3.5.1-1.el6.x86_64                                                                                                                                              4/9
  Verifying  : libtirpc-0.2.1-6.el6_5.2.x86_64                                                                                                                                                5/9
  Verifying  : glusterfs-libs-3.5.1-1.el6.x86_64                                                                                                                                              6/9
  Verifying  : libgssglue-0.1-11.el6.x86_64                                                                                                                                                   7/9
  Verifying  : glusterfs-3.5.1-1.el6.x86_64                                                                                                                                                   8/9
  Verifying  : glusterfs-server-3.5.1-1.el6.x86_64                                                                                                                                            9/9

Installed:
  glusterfs-server.x86_64 0:3.5.1-1.el6

Dependency Installed:
  glusterfs.x86_64 0:3.5.1-1.el6     glusterfs-api.x86_64 0:3.5.1-1.el6     glusterfs-cli.x86_64 0:3.5.1-1.el6     glusterfs-fuse.x86_64 0:3.5.1-1.el6     glusterfs-libs.x86_64 0:3.5.1-1.el6
  libgssglue.x86_64 0:0.1-11.el6     libtirpc.x86_64 0:0.2.1-6.el6_5.2      rpcbind.x86_64 0:0.2.0-11.el6

Complete!
[root@localhost ~]#
</pre>

**If you only like to install the client you install that with:**

<pre class="lang:default decode:true" title="glusterfs-client">yum isntall glusterfs-client</pre>

5. Now let&#8217;s make glusterfs start on reboot:

<pre class="lang:default decode:true" title="chkconfig start gluster deamon on user level 2,3,5">chkconfig --level 235 glusterd on</pre>

6. Time to start  GlusterFS

<pre class="lang:default decode:true" title="Command to start GlusterFS">service glusterd start</pre>

<pre class="lang:default decode:true" title="Output:">Starting glusterd:                                         [  OK  ]
</pre>

> GlusterFS is an open source, distributed file system capable of scaling to several petabytes (actually, 72 brontobytes!) and handling thousands of clients. GlusterFS clusters together storage building blocks over Infiniband RDMA or TCP/IP interconnect, aggregating disk and memory resources and managing data in a single global namespace. GlusterFS is based on a stackable user space design and can deliver exceptional performance for diverse workloads.
> 
>![](http://www.gluster.org/wp-content/uploads/2011/05/diagram-glusterfs.png) 
> 
> Figure 1. GlusterFS – One Common Mount Point
> 
> GlusterFS supports standard clients running standard applications over any standard IP network. Figure 1, above, illustrates how users can access application data and files in a Global namespace using a variety of standard protocols.
> 
> No longer are users locked into costly, monolithic, legacy storage platforms. GlusterFS gives users the ability to deploy scale-out, virtualized storage – scaling from terabytes to petabytes in a centrally managed and commoditized pool of storage.
> 
> Attributes of GlusterFS include:
> 
> <ul class="arrows">
>   <li>
>     Scalability and Performance
>   </li>
>   <li>
>     High Availability
>   </li>
>   <li>
>     Global Namespace
>   </li>
>   <li>
>     Elastic Hash Algorithm
>   </li>
>   <li>
>     Elastic Volume Manager
>   </li>
>   <li>
>     Gluster Console Manager
>   </li>
>   <li>
>     Standards-based
>   </li>
> </ul>
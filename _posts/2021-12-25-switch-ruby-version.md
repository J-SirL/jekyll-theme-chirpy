---
title: "HowTo switch to older ruby versions using DNF Modules"
date: 2021-12-25 02:17
category:
  - Linux
  - Jekyll
  - GitHubPages 
author: 
tags:
  - RHEL
  - CentOS
  - Fedora
  - Rocky Linux
  - AlmaLinux
  - Jekyll
  - Ruby
  - GitHubPages
  - Development
  - DNF
  - "DNF module"
summary: ""
---

The default ruby version that comes with Fedora, from fedora version 34 is Ruby version 3.x. This can cause issues if yoy are using projects or services that rely on older versions. For example at the time of writing github pages are relying on Ruby version 2.7

Fortunally it's easy to downgrade ruby on Fedora and other DNF or YUM distros. To do this we use DNF module or YUM module.

First you have to reset Ruby 
```bash
 $ sudo dnf module reset ruby
```
Then you can choose the Ruby version you like to install instead
```bash
sudo dnf module install ruby:2.7
```
If that dosen't work then set the allowerasing flag
```bash
sudo dnf module install ruby:2.7 --allowerasing
```
Then you should sync all packages with distro-sync
```bash
sudo dnf distro-sync --allowerasing
```

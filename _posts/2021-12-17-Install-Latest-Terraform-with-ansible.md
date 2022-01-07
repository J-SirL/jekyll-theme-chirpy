---
title: "Install latest terraform with ansible"
categories:
  - Infrastructure as code
  - Terraform
  - Linux
  - Latest
tags:
  - terraform
  - linux
  - rhel
  - Ffedora
  - arch
  - debian
  - ubuntu
  - alma linux
  - rocky linux
  - centos
  - iac
  - ansible
last_modified_at:
pin: True
---

<!-- ABOUT THE PROJECT -->
## What is Install Terraform

> Install Terraform is a project that installs latest Terraform using Ansible
This project started because I needed a fast way to check for new terraform versions, and got annoyed by all manual installation howTo's
so I decided to put it up for others to use.
It's very simple just clone the repository and run the command below and you have terraform on your system. 
 ```console
  ansible-playbook install_or_update_terraform.yml
 ``` 

It works with most Linux distributions

**AlmaLinux / Rocky Linux / Ubuntu / Debian / CentOS / Fedora / Arch Linux system etc.**

<!-- ABOUT TERRAFORM -->
## About Terraform by HashiCorp
> Terraform is an infrastructure as code (IaC) tool that allows you to build, change, and version infrastructure safely and efficiently. This includes low-level components such as compute instances, storage, and networking, as well as high-level components such as DNS entries, SaaS features, etc. Terraform can manage both existing service providers and custom in-house solutions.
 
> Key Features of Terraform
Infrastructure as Code
You describe your infrastructure using Terraform's high-level configuration language in human-readable, declarative configuration files. This allows you to create a blueprint that you can version, share, and reuse.
 
> Execution Plans
Terraform generates an execution plan describing what it will do and asks for your approval before making any infrastructure changes. This allows you to review changes before Terraform creates, updates, or destroys infrastructure.
 
> Resource Graph
Terraform builds a resource graph and creates or modifies non-dependent resources in parallel. This allows Terraform to build resources as efficiently as possible and gives you greater insight into your infrastructure.
 
> Change Automation
Terraform can apply complex changesets to your infrastructure with minimal human interaction. When you update configuration files, Terraform determines what changed and creates incremental execution plans that respect dependencies.

<!-- GETTING STARTED -->
## Getting Started

### Clone project

```console
git clone https://github.com/J-SirL/install_terraform.git
```
### Change to project folder

```console
cd install_terraform/PlayBooks
```

### Inventory

 **Either create a [terraform] group in the inventory or change hosts to all in playbook**

```yaml
[terraform]
# use fqdn or the ip address of the system where you want to install terraform
terraformclient.example.com 
```
{: .nolineno}

### Run it with ansible-playbook

```console 
ansible-playbook install_or_update_terraform.yml
```
<br>**Alternatively run it with a speciffic inventory file**
```console
ansible-playbook -i inventory install_or_update_terraform.yml
```


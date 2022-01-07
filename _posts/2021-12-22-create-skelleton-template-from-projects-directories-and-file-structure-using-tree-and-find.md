---
title: "Create skelleton template from project directories and file structure using tree, find and xagrgs commands"
date: 2021-12-22 23:09
category:
  - Linux
author: 
tags: 
  - tree
  - xagrgs
  - find
  - skelleton
  - template
summary: "Your customer has requested your help to create a direcory and files template of an existing project.
 Customer wants the directory structure and file names to be the same but do not want any of the file content to be present they just want the skelleton template of the project stucture. To solve this we need to create two files one with the directory stucture and one file with the files."  
---

## Example Use case

Your customer has requested your help to create a direcory and files skelleton template structure of an existing project.
Customer wants the directory structure and file names to be the same but do not want any of the file content to be present they just want the skelleton template of the project stucture.

To solve this we need to create two files one that contains the directory stucture and one file that contains the filenames that needs to be created. We solve this using the tree command. First we create the file that are only listing the directory structure.

### Project requirements

As seen below in our example the customers project folders are located in `~/Ansible_Projects/`
The customer wants us to create a skelleton template of the project **install_terraform**
 ```bash
 .
 ├── ansible-collection-hardening
 ├── awx
 ├── awx-operator
 ├── folder_to_template
 ├── install_terraform
 ├── kvm-deploy-ansible
 ├── my_test_driven_developments
 └── netbox-examples
 ```
 {: .nolineno}
 {: file="../Ansible_Projects/" }

### Output folder

The customer wants us to put the generated text files in
<br>
`~/output`

### Project naming standard

`project_project_name_dir.txt` - the directory structure file
<br>
`project_project_name_files.txt` - the projects file

`~/skelleton_project_templates/project_name/` - the skelleton project structure

### Files and directores to be created

Based on the naming standard that the client has set we will create the following project directory and files. 

`~/skelleton_project_templates/install_terraform/` - skelleton project directory
<br>
`project_install_terraform_dir.txt` - filename for the directory structure 
<br> 
`project_install_terraform_files_.txt` - filename for the project files

Now when we have the projects requirements set, we can start to create it.

## Create the requested folders

### Output folder

```shell
mkdir ~/output
```
{: .nolineno}

### Skelleton project folder

```bash
mkdir -p ~/skelleton_project_templates/install_terraform/
```
{: .nolineno}


## Create the template files

### cd into ~/Ansible_Projects

```bash
cd  ~/Ansible_Projects
```
{: .nolineno}


### Create the directory structure template using tree

```bash
tree  install_terraform -dfiUR --noreport > ~/output/project_install_terraform_dir.txt | sed -i '1d' ~/output/project_install_terraform_dir.txt
```
{: .nolineno}


### Create the files template using tree

```bash
tree install_terraform -IfiUR '.git|.terraform|.gitignore' --noreport  > ~/output/project_install_terraform_files_.txt 
```
{: .nolineno}


--- 

## Finally create the skelleton project using xargs

### cd into the template project stucture

```bash
cd ~/skelleton_project_templates/install_terraform/
```
{: .nolineno}

### Create the directory structure with xargs

```bash
xargs -I {} mkdir -p "{}" <  ~/output/project_install_terraform_dir.txt
```
{: .nolineno}

### Create the file structure with xargs

```bash
xargs -d'\n' touch < ~/output/project_install_terraform_files_.txt 
```
{: .nolineno}

## Example finished skelleton template

```bash
.
└── install_terraform
    ├── blank.md
    ├── inventory
    │   ├── dynamic_kvm_inventory.yml
    │   └── libvirt_lxc.yml
    ├── kvm_multiply_machines
    │   ├── cloud_init_centos.8.cfg
    │   ├── libvirt.tf
    │   ├── network_config_dhcp.cfg
    │   ├── state
    │   │   └── multiple_machines.tfstate
    │   ├── terraform.tfstate
    │   └── terraform.tfstate.backup
    ├── kvm_terraform
    │   ├── config
    │   │   └── cloud_init.yml
    │   ├── id_rsa
    │   ├── id_rsa.pub
    │   ├── libvirt.tf
    │   ├── main.tf
    │   ├── outputs.tf
    │   ├── terraform.tfstate
    │   └── terraform.tfstate.backup
    ├── local_test.yml
    ├── PlayBooks
    │   ├── check_update_needed.yml
    │   ├── collec_a_few_facts.yml
    │   ├── get_latest_release.yml
    │   ├── install_or_update_terraform.yml
    │   ├── install_terraform.yml
    │   ├── inv
    │   ├── list_vms.yml
    │   └── test_libvirt_inventory_plugin.yml
    ├── README.md
    └── terragrunt_project_test
```
{: .nolineno}

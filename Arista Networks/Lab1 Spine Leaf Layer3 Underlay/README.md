## Introduction

Lab 1 is the first lab of ***Network Automation with Ansible*** lab series on Arista Networks.

Lab 1 covers the following tasks which are applied on Arista nodes of Spine Leaf Layer3 Underlay network:
 - Checks:
   - Display name values defined in YAML-format inventory file. These name values can be different than the actual hostnames configured on Arista nodes.
 - Configurations:
   - `banner login` and `banner motd`

## Requirements
- **Control node**
  - One control node where ansible is installed.

- **Managed nodes**
  - Six managed nodes, also known as **target nodes**, where the configuration changes or modifications are applied:
    - Two spine nodes
    - Four leaf nodes
- **Network connectivity**
  - Control node must be able to reach managed nodes via SSH.
  - Network segmentation:
    - Control node and managed nodes are either in the same Layer 2 network segment (without any routed devices in between) or in differrent network segments (with one or more routed devices in between).

## Project Structure
The below code snippet reveals the structure of this Lab 1. The command `tree -L 1` show the current directory and its immediate sub-directories (Depth 1 or Level 1)  
 ```
 ansible-arista$ tree -L 1
 .
 ├── ansible.cfg
 ├── group_vars
 ├── host_inventory.yml
 ├── playbook_display_name.yml
 ```
File `ansible.cfg`:
```
ansible-arista$ cat ansible.cfg
[defaults]
inventory=host_inventory.yml
gathering = explicit
host_key_checking = False
```

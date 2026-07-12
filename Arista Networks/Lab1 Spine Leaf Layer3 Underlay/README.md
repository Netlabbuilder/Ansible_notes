## Introduction

Lab 1 is the first lab of ***Network Automation with Ansible*** lab series on Arista Networks.

Lab 1 covers the following configuration tasks which are applied on Arista nodes of Spine Leaf Layer3 Underlay network:
 - `banner login` and `banner motd`
 - `dns domain`
 - `ip name-server`

## Requirements
- **Control node**
  - One control node on which ansible is installed.

- **Managed nodes**
  - Six managed nodes, also known as **target nodes**, on which the configuration changes or modifications are applied:
    - Two spine nodes
    - Four leaf nodes
- **Network connectivity**
  - Control node must be able to reach managed nodes via SSH.
  - Network segmentation:
    - Control node and managed nodes are either in the same Layer 2 network segment (without any routed devices in between) or in differrent network segments (with one or more routed devices in between).

## Project Structure
The below code snippets reveal the proposed structure of this Lab 1.

The command `tree -L 2` show the content of current directory and the content of its immediate sub-directories (Depth 2 or Level 2)  
 ```
 ansible-arista$ tree -L 2
 .
 ├── ansible.cfg
 ├── group_vars
 │   └── arista_ceos.yml
 ├── host_inventory.yml
 ├── playbook_config_banner_login.yml
 ├── playbook_display_name.yml
 ```
## Playbooks
**Playbook 1:** `playbook_display_name.yml`
- Run the playbook for the first time with command `ansible-playbook playbook_config_banner_login.yml`:
  
  ```
  ansible-arista$ ansible-playbook playbook_display_name.yml
  
  PLAY [Display configurations on Arista nodes] ******************************************************************************
  
  TASK [Display name values declared in YAML-format inventory file (`host_inventory.yml`) by using ansible default variable 'inventory_hostname'] ***
  ok: [spine1] => {
      "msg": "“Hostname is spine1”"
  }
  ok: [leaf2] => {
      "msg": "“Hostname is leaf2”"
  }
  ok: [leaf3] => {
      "msg": "“Hostname is leaf3”"
  }
  ok: [leaf1] => {
      "msg": "“Hostname is leaf1”"
  }
  ok: [spine2] => {
      "msg": "“Hostname is spine2”"
  }
  ok: [leaf4] => {
      "msg": "“Hostname is leaf4”"
  }
  
  PLAY RECAP *****************************************************************************************************************
  leaf1                      : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
  leaf2                      : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
  leaf3                      : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
  leaf4                      : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
  spine1                     : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
  spine2                     : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
  
  ansible-arista$
  ```
  - Because this playbook is to display the configurations on target nodes, `TASK` section shows `ok: [spine1]`, `ok: [leaf2]`, `ok: [leaf3]`, `ok: [leaf1]`, `ok: [spine2]` and `ok: [leaf4]`, which indicates no changes occurred. `PLAY RECAP` section reaffirms it by showing `changed=0`.

**Playbook 2:** `playbook_config_banner_login.yml`

- Run the playbook for the first time with command `ansible-playbook playbook_config_banner_login.yml`:

    ```
    ansible-arista$ ansible-playbook playbook_config_banner_login.yml
    
    PLAY [Apply configurations on Arista nodes] ********************************************************************************
    
    TASK [Configure `banner login`] ********************************************************************************************
    changed: [leaf1]
    changed: [spine1]
    changed: [leaf3]
    changed: [spine2]
    changed: [leaf2]
    changed: [leaf4]
    
    PLAY RECAP *****************************************************************************************************************
    leaf1                      : ok=1    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
    leaf2                      : ok=1    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
    leaf3                      : ok=1    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
    leaf4                      : ok=1    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
    spine1                     : ok=1    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
    spine2                     : ok=1    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
    
    ansible-arista$
    ```
  - Before the playbook 2 executed, there were no `banner login` configurations on target nodes. The playbook 2 checked and then applied the desired banner login strings and lines.
  - `TASK` section shows `changed: [leaf1]`, `changed: [spine1]`, `changed: [leaf3]`, `changed: [spine2]`, `changed: [leaf2]` and `changed: [leaf4]`; and `PLAY RECAP` section shows `changed=1` as there was only one change on each device.
- Run the same playbook one more time:
  
    ```
    ansible-arista$ ansible-playbook playbook_config_banner_login.yml
    
    PLAY [Apply configurations on Arista nodes] ********************************************************************************
    
    TASK [Configure `banner login`] ********************************************************************************************
    ok: [spine1]
    ok: [leaf1]
    ok: [spine2]
    ok: [leaf3]
    ok: [leaf2]
    ok: [leaf4]
    
    PLAY RECAP *****************************************************************************************************************
    leaf1                      : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
    leaf2                      : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
    leaf3                      : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
    leaf4                      : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
    spine1                     : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
    spine2                     : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
    
    ansible-arista$
    ```
- Verify the banner login strings and lines are now present on target nodes:
  ```
  ansible-arista$ ssh admin@leaf1
  Warning: Permanently added 'leaf1' (ED25519) to the list of known hosts.
  WELCOME TO NETLABBUILDER.NET NETWORK INFRASTRUCTURE
  THIS SYSTEM IS RESTRICTED TO AUTHORIZED PERSONNEL ONLY
  (admin@leaf1) Password:
  
  ansible-arista$ ssh admin@leaf4
  Warning: Permanently added 'leaf4' (ED25519) to the list of known hosts.
  WELCOME TO NETLABBUILDER.NET NETWORK INFRASTRUCTURE
  THIS SYSTEM IS RESTRICTED TO AUTHORIZED PERSONNEL ONLY
  (admin@leaf4) Password:

  ansible-arista$ ssh admin@spine1
  Warning: Permanently added 'spine1' (ED25519) to the list of known hosts.
  WELCOME TO NETLABBUILDER.NET NETWORK INFRASTRUCTURE
  THIS SYSTEM IS RESTRICTED TO AUTHORIZED PERSONNEL ONLY
  (admin@spine1) Password:
  
  ansible-arista$
  ```

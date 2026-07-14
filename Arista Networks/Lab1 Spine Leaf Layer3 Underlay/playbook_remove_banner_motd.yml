---
- name: Remove configurations on Arista nodes
  hosts: all
  gather_facts: no
  tasks:
    - name: Remove `banner motd`      
      arista.eos.eos_banner:
        banner: motd
        state: absent

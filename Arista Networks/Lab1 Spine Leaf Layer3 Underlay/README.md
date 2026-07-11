## Introduction

Lab 1 is the first lab of ***Network Automation with Ansible*** lab series on Arista Networks.

Lab 1 covers the following configurations of Layer 3 Spine Leaf network:
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

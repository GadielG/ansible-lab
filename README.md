# Ansible Lab

This project is an **Ansible playbooks lab** using **Ubuntu Server virtual machines**. The purpose is to gain hands-on experience with **virtualization, Ubuntu Server OS, and automated deployment** of machines using Ansible. This experience is highly relevant for IT and cybersecurity environments.

---

## Initial Project Setup

The lab is built using **UTM**, a hypervisor optimized for Apple Silicon hosts. The lab consists of **3 Ubuntu Server VMs**:

- **Controller VM**  
  - 2 CPU cores  
  - 3 GB RAM  
  - 20 GB Storage  

- **Target VMs** (2 total)  
  - 1 CPU core each  
  - 1.5 GB RAM each  
  - 10 GB Storage each  

This was my first experience with **Ubuntu Server**. The installation process was straightforward, though the initial boot of the controller VM triggered the following error: "Failed unmounting cdrom.mount - /cdrom"


After troubleshooting, I **shut down the VM, removed the USB drive attached to the guest, and restarted the VM**, allowing it to boot successfully. Subsequent installations and first boots of the target VMs proceeded without issue.

---

## Networking Setup

For networking, the VMs use the **Shared Network** option in UTM. After configuration:

- All three VMs received **unique IP addresses** on the same subnet  
- I verified that **all VMs can ping each other**, confirming proper connectivity for automation  
- IP addresses and subnet information were recorded for inventory use in Ansible

---

## SSH and Ansible Setup

- Configured **SSH key-based authentication** from the Controller to all Target VMs  
- Verified connectivity using Ansible:  ansible all -i inventory/hosts.ini -m ping

Expected output:

192.168.64.12 | SUCCESS => {"changed": false, "ping": "pong"}
192.168.64.13 | SUCCESS => {"changed": false, "ping": "pong"}
Both Target VMs responded successfully, confirming remote control from Ansible.

---

## Playbooks

The first automation playbooks were created to:

Test connectivity (ping_test.yml)

Deploy and start Nginx on both Target VMs (install_nginx.yml)

Example playbook run:

ansible-playbook -i inventory/hosts.ini playbooks/install_nginx.yml --ask-become-pass

This executed successfully on both targets, demonstrating privilege escalation and automated deployment.

---
## Current Milestones

✅ Built and booted 3 functional Ubuntu Server VMs

✅ Fixed initial boot error (/cdrom unmount)

✅ Established network connectivity across all VMs

✅ Configured SSH access and verified Ansible connectivity

✅ Successfully ran Ansible playbooks on multiple targets

---

This README documents the lab setup, networking configuration, and initial deployment plan. Screenshots, diagrams, and playbooks are included in the repository to provide a complete, portfolio-ready demonstration of automated system deployment using Ansible on Ubuntu Server.



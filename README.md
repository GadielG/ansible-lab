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

## Next Steps

1. Fully **update and install Ansible** on the Controller VM  
2. Configure **SSH access** from the Controller to all Target VMs  
3. Create the **first Ansible playbook** to test connectivity (ping test) between Controller and Targets  
4. Create the **first deployment playbook**, installing **Nginx** on each Target using Ansible

---

## Future Enhancements

- Implement **multi-tier deployments** (e.g., web + database)  
- Introduce **variable-based playbooks** and **templates** for dynamic configuration  
- Add **security hardening tasks** (firewalls, user management)  
- Integrate **version control** using GitHub for playbook management  

---

This README documents the lab setup, networking configuration, and initial deployment plan. Screenshots, diagrams, and playbooks are included in the repository to provide a complete, portfolio-ready demonstration of automated system deployment using Ansible on Ubuntu Server.



# 02-Ubuntu-Server-Installation.md

# Ubuntu Server Installation on Proxmox VE

## Overview

This document outlines the deployment and initial configuration of an Ubuntu Server virtual machine within Proxmox Virtual Environment (VE). The Ubuntu Server VM provides a Linux environment for future self-hosted applications, server administration practice, and additional homelab services.

---

# Objectives

* Deploy Ubuntu Server as a virtual machine in Proxmox VE
* Configure virtual hardware resources
* Install Ubuntu Server LTS
* Configure networking
* Enable remote administration with OpenSSH
* Update the operating system
* Verify successful installation and connectivity

---

# Environment

| Component              | Details           |
| ---------------------- | ----------------- |
| Hypervisor             | Proxmox VE        |
| Guest Operating System | Ubuntu Server LTS |
| Virtualization         | KVM               |
| Installation Media     | Ubuntu Server ISO |
| Network Bridge         | vmbr0             |

---

# Virtual Machine Configuration

| Setting         | Value                               |
| --------------- | ----------------------------------- |
| VM Name         | Ubuntu-Server                       |
| CPU             | 2 | 1 socket, 2 cores               |
| Memory          | 4096 MB                             |
| Storage         | 32 GB                               |
| Disk Controller | VirtIO SCSI                         |
| Network Adapter | VirtIO                              |
| Bridge          | vmbr0                               |

---

# Creating the Virtual Machine

1. Log in to the Proxmox web interface.
2. Select the Proxmox node.
3. Click **Create VM**.
4. Enter the virtual machine name.
5. Select the Ubuntu Server ISO.
6. Configure the virtual hard disk.
7. Allocate CPU cores and memory.
8. Configure the network adapter.
9. Review the configuration.
10. Click **Finish**.

---

# Ubuntu Server Installation

Power on the virtual machine and complete the Ubuntu Server installation.

Configuration used during installation:

| Setting               | Value                               |
| --------------------- | ----------------------------------- |
| Language              | English                             |
| Keyboard Layout       | English (US)                        |
| Installation Type     | Ubuntu Server                       |
| Network Configuration | DHCP                                |
| Storage Layout        | Guided Storage                      |
| Hostname              | ubuntu-server                       |
| Administrative User   | *aidan*                             |
| OpenSSH Server        | Installed                           |

After the installation completed, the virtual machine rebooted into the newly installed operating system.

---

# System Updates

Update the package repository:

```bash
sudo apt update
```

Upgrade installed packages:

```bash
sudo apt upgrade -y
```

Remove unnecessary packages:

```bash
sudo apt autoremove -y
```

---

# Network Verification

Verify the assigned IP address:

```bash
ip address
```

View routing information:

```bash
ip route
```

Verify DNS configuration:

```bash
cat /etc/resolv.conf
```

Test Internet connectivity:

```bash
ping 8.8.8.8
```

Verify DNS resolution:

```bash
ping google.com
```

---

# SSH Configuration

OpenSSH Server was installed during the Ubuntu installation process to allow secure remote administration.

Verify that the SSH service is running:

```bash
sudo systemctl status ssh
```

Display the server IP address:

```bash
hostname -I
```

Connect remotely from another computer:

```bash
ssh username@server-ip
```

---

# Validation

The installation was verified by confirming:

* Ubuntu Server booted successfully.
* Administrative login completed successfully.
* Network connectivity was established.
* Internet access was available.
* DNS resolution functioned correctly.
* System packages were successfully updated.
* SSH service was running and accepting remote connections.

---

# Troubleshooting

## No Internet Connection

* Verify the virtual network adapter is connected to the correct Proxmox bridge.
* Confirm DHCP or static IP settings.
* Verify the default gateway.

---

## DNS Resolution Fails

Verify the configured DNS server:

```bash
cat /etc/resolv.conf
```

Test external connectivity:

```bash
ping 8.8.8.8
```

If the IP responds but domain names do not, verify the DNS configuration.

---

## SSH Connection Failed

Verify that SSH is running:

```bash
sudo systemctl status ssh
```

If necessary, start the service:

```bash
sudo systemctl start ssh
```

---

# Lessons Learned

This project provided hands-on experience with:

* Creating virtual machines in Proxmox VE
* Installing Ubuntu Server LTS
* Allocating virtual hardware resources
* Configuring Linux networking
* Managing software packages with APT
* Enabling secure remote administration using OpenSSH
* Verifying system functionality after installation

---

# Future Enhancements

This Ubuntu Server will serve as the foundation for future homelab services, including:

* Docker
* Portainer
* Nginx Reverse Proxy
* Plex Media Server
* Jellyfin
* Monitoring tools
* Automation scripts
* Additional Linux server projects

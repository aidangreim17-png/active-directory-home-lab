# 01 - Proxmox VE Deployment

## Project Overview

This project established the virtualization platform used to host the enterprise homelab. Proxmox VE was selected as the hypervisor to provide centralized virtual machine management, snapshots, virtual networking, and resource allocation for Windows and Linux servers.

---

# Objectives

* Deploy Proxmox VE as the primary hypervisor
* Configure storage for virtual machines
* Configure virtual networking
* Create the foundation for enterprise infrastructure
* Host Windows Server, Windows 11, Ubuntu Server, and pfSense virtual machines

---

# Environment

| Component            | Value                |
| -------------------- | -------------------- |
| Hypervisor           | Proxmox VE 9.2.3     |
| Installation Type    | Bare Metal           |
| Management Interface | Web Interface        |
| Storage              | local / local-lvm    |
| Virtual Networking   | Linux Bridge (vmbr0) |

---

# Hardware

| Component | Specification      |
| --------- | ------------------ |
| CPU       | *Intel Core i5-8500*   |
| Memory    | *16 GB*    |
| Storage   | *500 GB* |
| Network   | 10 Gigabit Ethernet   |

---

# Network Configuration

```text
Internet
      │
Home Router
      │
Proxmox Host
      │
vmbr0
      │
──────────────────────────────
│        │        │         │
pfSense Ubuntu   DC01   CLIENT01
```

---

# Virtual Machines

## pfSense

Purpose

* Firewall
* Router
* DHCP
* Gateway

---

## Ubuntu Server

Purpose

* Docker Host
* Portainer
* Pi-hole

---

## Windows Server 2025

Hostname

DC01

Purpose

* Active Directory
* DNS
* Group Policy
* File Server

---

## Windows 11

Hostname

CLIENT01

Purpose

* Domain Workstation
* Group Policy Testing
* Software Deployment Testing

---

# Storage Configuration

Configured virtual disks using:

* VirtIO SCSI Controller
* Thin Provisioning
* Local-LVM Storage

Snapshots were created before major configuration changes to provide rollback capability.

---

# Virtual Networking

Configured Linux Bridge networking allowing all virtual machines to communicate on the internal network while using pfSense as the primary gateway.

---

# Management Features Used

* Virtual Machines
* Snapshots
* Hardware Configuration
* ISO Management
* Console Access
* Storage Management
* Virtual Networking

---

# Troubleshooting

## VirtIO Drivers

### Issue

Windows installation could not detect the virtual disk.

### Resolution

Mounted the VirtIO ISO and loaded the VirtIO storage driver during Windows Setup.

---

## VirtIO Network Driver

### Issue

Windows virtual machine completed installation without network connectivity.

### Resolution

Installed the VirtIO network driver from the VirtIO ISO after Windows installation.

---

## Thin Provisioning Warning

### Issue

While creating VM snapshots, Proxmox displayed warnings indicating the total allocated virtual disk capacity exceeded the physical size of the thin pool.

### Resolution

Verified this was expected behavior due to thin provisioning. Continued monitoring storage utilization and retained snapshots only when necessary.

---

# Validation

Successfully deployed and managed the following virtual machines:

* pfSense
* Ubuntu Server
* Windows Server 2025
* Windows 11

Verified:

* VM startup
* Network connectivity
* Snapshot functionality
* Storage allocation
* Console access

---

# Skills Demonstrated

* Proxmox VE Administration
* Hypervisor Management
* Virtual Machine Deployment
* Virtual Networking
* Storage Management
* Snapshot Management
* Windows Virtualization
* Linux Virtualization
* Enterprise Infrastructure Planning

---

# Lessons Learned

Deploying Proxmox VE provided hands-on experience with enterprise virtualization concepts including virtual networking, storage management, snapshots, and resource allocation. The platform became the foundation for all subsequent Windows and Linux infrastructure projects completed throughout this homelab.

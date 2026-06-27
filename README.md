# Enterprise Home Lab

## Overview

This project documents the design, deployment, and administration of a Windows enterprise home lab hosted on Proxmox VE. The lab simulates a small business environment by combining virtualization, networking, Linux services, Active Directory, Group Policy, centralized software deployment, and Windows administration.

## Technologies

- Proxmox VE 9.2.3
- pfSense
- Ubuntu Server
- Docker
- Portainer
- Pi-hole
- Windows Server 2025
- Active Directory Domain Services
- DNS
- Group Policy
- Windows 11
- SMB File Sharing
- NTFS Permissions
- PowerShell

---

## Lab Architecture

```text
Internet
     │
Home Router
     │
pfSense Firewall
192.168.50.1
│
├───────────────┐
│               │
Ubuntu       Windows Server 2025
Server           DC01
│                │
Docker           Active Directory
Portainer        DNS
Pi-hole
│                │
└──────────────┐
               │
         Windows 11
          CLIENT01
```

---

## Completed Projects

- [x] Proxmox VE Installation
- [x] pfSense Configuration
- [x] Ubuntu Server
- [x] Docker & Portainer
- [x] Pi-hole DNS
- [x] Windows 11 Deployment
- [x] Windows Server 2025 Deployment
- [x] Active Directory
- [x] DNS
- [x] Organizational Units
- [x] Users & Groups
- [x] Domain Join
- [x] Wallpaper Group Policy
- [x] Department File Shares
- [x] NTFS Permissions
- [x] Drive Mapping
- [x] Password Policies
- [x] Account Lockout Policies
- [x] Software Deployment

---

## Skills Demonstrated

- Windows Server Administration
- Active Directory
- DNS Administration
- Group Policy
- SMB Shares
- NTFS Permissions
- Windows Deployment
- Enterprise Troubleshooting
- Virtualization
- Linux Administration
- Network Administration
- PowerShell

# active-directory-home-lab
Simulated a small business Windows network using Active Directory, DNS, DHCP, Group Policy, and domain-joined Windows 11 clients.

# Active Directory Home Lab

## Overview

Built a Windows Server 2022 Active Directory lab to simulate a small business environment. The project includes centralized authentication, DNS, DHCP, Group Policy, file sharing, and Windows 11 domain clients while demonstrating common Help Desk and Junior Systems Administrator tasks.

---

## Technologies Used

- Windows Server 2022
- Windows 11 Pro
- Oracle VirtualBox
- Active Directory Domain Services
- DNS
- DHCP
- Group Policy
- NTFS Permissions
- SMB File Shares

---

## Environment

### Domain Controller

- Windows Server 2022
- Active Directory
- DNS
- DHCP
- File Services
- Group Policy

### Client Machines

- Windows 11 Pro
- Domain Joined

---

## Features

- Active Directory domain deployment
- Organizational Units
- User and group management
- Security groups
- NTFS permissions
- Shared folders
- Group Policy deployment
- Drive Mapping GPO
- Wallpaper GPO
- DHCP Server
- DNS Server
- Password resets
- Account lockout recovery
- Account disable/enable
- Role-Based Access Control (RBAC)

---

## Skills Demonstrated

- Windows Server Administration
- Active Directory Administration
- DNS Management
- DHCP Deployment
- Group Policy Management
- Windows Troubleshooting
- Authentication Troubleshooting
- Network Troubleshooting
- File Server Administration

---

## Troubleshooting Highlights

### DNS Issues

- Diagnosed DNS timeouts
- Verified SRV records
- Restarted DNS service
- Validated Active Directory registration

### Group Policy

- Used gpresult and RSOP
- Resolved conflicting GPO settings
- Fixed wallpaper deployment
- Troubleshot profile corruption

### DHCP

- Installed and authorized DHCP
- Created IPv4 scope
- Configured exclusions
- Validated leases

### File Shares

- Configured NTFS and Share permissions
- Tested departmental access
- Implemented RBAC

---

## Screenshots

### Active Directory Users and Computers

![AD Users](screenshots/ad-users/HR.png)
![AD Users](screenshots/ad-users/IT.png)
![AD Users](screenshots/ad-users/Sales.png)

### DHCP Scope

![DHCP](screenshots/dhcp/dhcp-pool.png)

### Drive Mapping GPO

![Drive Mapping](screenshots/gpo-drive-map.png)

### Wallpaper Policy

![Wallpaper](screenshots/wallpaper-gpo.png)

### File Shares

![Shares](screenshots/file-shares.png)

---

## Lessons Learned

- Active Directory relies heavily on DNS.
- Windows Firewall can block domain communication.
- Group Policy conflicts require RSOP for troubleshooting.
- NTFS and Share permissions must both be configured.
- Methodical troubleshooting is more effective than changing multiple settings at once.

---

## Future Improvements

- WSUS Deployment
- Certificate Services (AD CS)
- Print Server
- Windows Deployment Services
- Multi-site Active Directory
- Azure AD Hybrid Join
- PowerShell Automation
- Backup and Restore

# 03-Windows-11-Installation.md

# Windows 11 Installation on Proxmox VE

## Overview

This document outlines the deployment and initial configuration of a Windows 11 virtual machine in Proxmox Virtual Environment (VE). The Windows 11 VM serves as a client workstation for Active Directory domain management, Group Policy testing, software deployment, file share access, and Windows administration.

---

# Objectives

* Create a Windows 11 virtual machine
* Install Windows 11 Pro
* Configure virtual hardware
* Install VirtIO drivers
* Configure networking
* Install the latest Windows updates
* Verify successful installation

---

# Environment

| Component              | Details           |
| ---------------------- | ----------------- |
| Hypervisor             | Proxmox VE        |
| Guest Operating System | Windows 11 Pro    |
| Virtualization         | KVM               |
| Installation Media     | Windows 11 ISO    |
| Additional Drivers     | VirtIO Driver ISO |

---

## Licensing

Windows 11 Pro was installed for educational and homelab purposes.


# Virtual Machine Configuration

| Setting         | Value                               |
| --------------- | ----------------------------------- |
| VM Name         | CLIENT01                            |
| CPU             | *2 (1 socket, 2 cores)*             |
| Memory          | *4096 MB*                           |
| Storage         | *64 GB*                             |
| Disk Controller | VirtIO SCSI                         |
| Network Adapter | VirtIO                              |
| Bridge          | vmbr0                               |
| BIOS            | OVMF (UEFI)                         |
| Machine Type    | q35                                 |
| TPM             | v2.0 Enabled                        |

---

# Creating the Virtual Machine

1. Logged onto the Proxmox web interface.
2. Selected the Proxmox node.
3. Clicked **Create VM**.
4. Assigned the virtual machine name.
5. Selected the Windows 11 ISO.
6. Attached the VirtIO Driver ISO.
7. Configured CPU, memory, and storage.
8. Configured the network adapter.
9. Enabled TPM 2.0 and UEFI.
10. Reviewed the configuration and created the VM.

---

# Installing Windows 11

Powered on the virtual machine and launched the Windows installation.

Configuration used during installation:

| Setting           | Value               |
| ----------------- | ------------------- |
| Edition           | Windows 11 Pro      |
| Keyboard Layout   | English (US)        |
| Time Zone         | *Eastern Time*      |
| Installation Type | Custom Installation |

During installation:

* Loaded VirtIO storage drivers.
* Selected the virtual disk.
* Completed Windows installation.
* Created the local administrator account.

---

## Bypassing Windows 11 Hardware Requirements

During the Windows installation, the built-in hardware checks were bypassed to allow installation in the virtual environment.

1. Pressed **Shift + F10** to open Command Prompt.
2. Launched the Registry Editor:

   regedit

3. Navigated to:

   HKEY_LOCAL_MACHINE\SYSTEM\Setup

4. Created a new key named:

   LabConfig

5. Created the following DWORD (32-bit) values and set each to **1**:

   - BypassTPMCheck
   - BypassSecureBootCheck
   - BypassRAMCheck

6. Closed Registry Editor and continue the Windows installation.


# Installing VirtIO Drivers

After Windows installation:

1. Mounted the VirtIO Driver ISO.
2. Installed the required drivers:

   * Storage
   * Network
   * Balloon
   * Guest Tools (if installed)
3. Restarted the virtual machine.

---

# Network Configuration

Verified the assigned IP address:

```powershell
ipconfig
```

Verified Internet connectivity:

```powershell
ping 8.8.8.8
```

Verified DNS resolution:

```powershell
ping google.com
```

---

# Windows Updates

Opened:

**Settings → Windows Update**

Installed all available updates until the system reports it is fully up to date.

---

## Driver Verification

Device Manager was reviewed after installation to verify that all required drivers were installed successfully.

Verification included:

- Storage Controller
- Network Adapter
- Display Adapter
- System Devices

No unknown devices or driver errors were present.


# Validation

The installation was verified by confirming:

* Windows 11 booted successfully.
* Network adapter functioned correctly.
* Internet connectivity was established.
* DNS resolution was operational.
* VirtIO drivers were installed successfully.
* Windows Update completed successfully.

---

# Troubleshooting

## Virtual Disk Not Detected

Cause:

VirtIO storage driver not loaded.

Resolution:

Loaded the appropriate VirtIO storage driver during Windows installation.

---

## No Network Connectivity

Verified:

* VirtIO network driver is installed.
* Correct bridge is selected in Proxmox.
* IP address assigned successfully.

---

## Windows 11 Hardware Requirements

If Windows Setup reports unsupported hardware:

* Verify TPM 2.0 is enabled.
* Verify UEFI (OVMF) is selected.
* Confirm Secure Boot configuration if required.

---

# Lessons Learned

This project provided hands-on experience with:

* Creating Windows virtual machines in Proxmox VE
* Configuring virtual hardware
* Installing Windows 11 Pro
* Installing VirtIO drivers
* Configuring Windows networking
* Applying Windows Updates
* Validating system functionality after deployment

---

# Future Enhancements

This Windows 11 virtual machine will be used to:

* Join an Active Directory domain
* Test Group Policy Objects (GPOs)
* Access shared network drives
* Validate software deployments
* Perform Windows administration tasks
* Simulate enterprise workstation management

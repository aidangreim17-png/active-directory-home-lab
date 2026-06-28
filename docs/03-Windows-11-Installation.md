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

1. Log into the Proxmox web interface.
2. Select the Proxmox node.
3. Click **Create VM**.
4. Assign the virtual machine name.
5. Select the Windows 11 ISO.
6. Attach the VirtIO Driver ISO.
7. Configure CPU, memory, and storage.
8. Configure the network adapter.
9. Enable TPM 2.0 and UEFI.
10. Review the configuration and create the VM.

---

# Installing Windows 11

Power on the virtual machine and launch the Windows installation.

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

1. Press **Shift + F10** to open Command Prompt.
2. Launch the Registry Editor:

   regedit

3. Navigate to:

   HKEY_LOCAL_MACHINE\SYSTEM\Setup

4. Create a new key named:

   LabConfig

5. Create the following DWORD (32-bit) values and set each to **1**:

   - BypassTPMCheck
   - BypassSecureBootCheck
   - BypassRAMCheck

6. Close Registry Editor and continue the Windows installation.


# Installing VirtIO Drivers

After Windows installation:

1. Mount the VirtIO Driver ISO.
2. Install the required drivers:

   * Storage
   * Network
   * Balloon
   * Guest Tools (if installed)
3. Restart the virtual machine.

---

# Network Configuration

Verify the assigned IP address:

```powershell
ipconfig
```

Verify Internet connectivity:

```powershell
ping 8.8.8.8
```

Verify DNS resolution:

```powershell
ping google.com
```

---

# Windows Updates

Open:

**Settings → Windows Update**

Install all available updates until the system reports it is fully up to date.

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

Load the appropriate VirtIO storage driver during Windows installation.

---

## No Network Connectivity

Verify:

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

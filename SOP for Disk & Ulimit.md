# Disk Usage & Ulimit Configuration on Ubuntu OS

###  Document Details

| Author           | Created    | Version | Last updated by  | Last Edited On | L0 Reviewer | L1 Reviewer | L2 Reviewer |
| ---------------- | ---------- | ------- | ---------------- | -------------- |----------- | ----------- | ----------- |
| Shreyas Awasthi | 2026-01-20 | 1.0     | Shreyas Awasthi | 2026-01-23     | Mohit Kumar        |   |       |
| Shreyas Awasthi | 2026-01-20 | 1.1     | Shreyas Awasthi | 2026-01-24    | Divya Mishra         |  Pritam |        |

---

## Table of Contents

1. [Purpose](#1-purpose)
2. [Scope](#2-scope)
3. [Prerequisites](#3-prerequisites)
4. [Procedure](#4-procedure)  
   4.1. [Check Disk Usage](#41-check-disk-usage)  
   &nbsp;&nbsp;&nbsp;4.1.1. [List All Mounted Filesystems & Usage](#411-list-all-mounted-filesystems--usage)  
   &nbsp;&nbsp;&nbsp;4.1.2. [Identify Top Disk Consumers](#412-identify-top-disk-consumers)  
   &nbsp;&nbsp;&nbsp;4.1.3. [Check Inode Usage](#413-check-inode-usage)  
   4.2. [Check and Manage Mount Points](#42-check-and-manage-mount-points)  
   &nbsp;&nbsp;&nbsp;4.2.1. [List Active Mounts](#421-list-active-mounts)   
   &nbsp;&nbsp;&nbsp;4.2.2 [Mount/Unmount Filesystems (if necessary)](#422-mountunmount-filesystems-if-necessary)  
   4.3. [Configure Ulimit Settings](#43-configure-ulimit-settings)  
   &nbsp;&nbsp;&nbsp;4.3.1. [Check Current Ulimit Values](#431-check-current-ulimit-values)  
   &nbsp;&nbsp;&nbsp;4.3.2. [Set Temporary Ulimit for Current Session](#432-set-temporary-ulimit-for-current-session)  
   &nbsp;&nbsp;&nbsp;4.3.3. [Configure Persistent Ulimits for Users](#433-configure-persistent-ulimits-for-users)  
5. [Conclusion](#5-conclusion)
6. [Contact Information](#6-contact-information)
7. [References](#7-references)
---

## 1. Purpose
This SOP outlines standardized procedures to:
- Check disk usage and mount points
- Configure and verify ulimit (user limits) settings for users and processes  
on Ubuntu-based systems, ensuring optimal system performance and resource usage.

---
## 2. Scope

Disk is the storage space where the operating system, applications, and files are permanently saved. If disk space is full, applications and the system may fail.

ulimit is a Linux command that restricts how much system resources a user or process can use, such as memory, CPU, and open files. It prevents one process from overusing system resources.

### Disk Usage Scope

The disk usage scope includes:

- **Monitoring filesystem utilization**  
  Ensures critical filesystems (such as `/`, `/var`, `/home`) remain within safe usage thresholds.
- **Identifying high disk consumption areas**  
  Helps locate large files or directories responsible for excessive disk usage.
- **Mount point verification and management**  
  Confirms that required filesystems are properly mounted and accessible.
**Out of Scope (Disk):**
- Advanced storage provisioning (RAID, LVM resizing)
- Filesystem repair or data recovery operations
  
### Ulimit Configuration Scope

The ulimit scope includes:

- **Reviewing current ulimit values**  
  Validates resource limits applied to users and running processes.
- **Setting temporary ulimit values**  
  Applies session-based limits for testing or short-term troubleshooting.
- **Configuring persistent user limits**  
  Ensures resource limits remain effective after reboot using `limits.conf`.
**Out of Scope (Ulimit):**
- Kernel parameter tuning (`sysctl`)
- Performance benchmarking or stress testing
---

## 3. Prerequisites

Before performing disk usage analysis and ulimit configuration, ensure the following prerequisites are met:

- **Operational access to the Ubuntu server**  
  SSH access with a user account that can switch to elevated privileges.
- **Sudo-level permissions**  
  Required to inspect mount points, manage disks, and apply persistent ulimit configurations.
- **Working knowledge of filesystem and process limits**  
  Understanding of filesystems, mount points, and resource limits such as open files (`nofile`) to avoid misconfiguration.
- **Awareness of application impact**  
  Knowledge of running services to ensure disk or ulimit changes do not disrupt active workloads.

---

## 4. Procedure

### 4.1 Check Disk Usage
This command is used to check how much disk space is available and how much is already used on the system.

It shows:
All mounted disks, Disk type, Total space, Used space and Free space.
The sizes are shown in an easy-to-read format (GB/MB), so anyone can quickly understand the storage status.

#### 4.1.1 List All Mounted Filesystems & Usage
```bash
df -hT
```
- **Purpose:** Displays all mounted filesystems with type and human-readable sizes.
- Ensure root (/) is not above 80% usage.
<img width="1664" height="824" alt="image" src="https://github.com/user-attachments/assets/1d0a9b1c-96ec-4b28-9f2e-ae6fa100e320" />

##### Check Disk Usage by Directory
```bash
du -sh /path/to/directory
```
<img width="1212" height="68" alt="image" src="https://github.com/user-attachments/assets/851a04fc-994a-4e92-aae4-66cdd441be0a" />


#### 4.1.2 Identify Top Disk Consumers
```bash
sudo du -ahx / | sort -rh | head -n 20
```
- **Purpose:** Lists top 20 largest files/directories on root (`/`).
- **Note:** Adjust the path as needed for specific mount points.

<img width="2350" height="624" alt="image" src="https://github.com/user-attachments/assets/2ae980d7-41dd-404d-ab01-1ba3a207ebe0" />


#### 4.1.3 Check Inode Usage
Inode usage shows how many files and folders are present on the disk. Even if free space is available, the system can face issues if all inodes are used.
```bash
df -i
```
- **Purpose:** Identifies inode exhaustion, which can cause "disk full" errors despite free space.

<img width="1820" height="822" alt="image" src="https://github.com/user-attachments/assets/ec404ff7-1c86-4a6c-a278-f179803f49ea" />

### 4.2 Check and Manage Mount Points

#### 4.2.1 List Active Mounts
It helps confirm which disks or directories are mounted and active on the system, useful for routine checks and troubleshooting.
```bash
mount | column -t
```
<img width="2026" height="910" alt="image" src="https://github.com/user-attachments/assets/8b9eb5f6-fbc3-4667-913c-0171f329aea9" />


or
```bash
lsblk -f
```
<img width="1914" height="272" alt="image" src="https://github.com/user-attachments/assets/86539db2-1636-4599-8482-32051bb388a1" />


- **Purpose:** Shows device, mount point, and filesystem type.


#### 4.2.2 Mount/Unmount Filesystems (if necessary)
Managing mount points means checking, attaching, or removing disks so the system can correctly access storage when needed.
- **Detect the New Disk in Ubuntu**
  ```bash
  lsblk
  ```
<img width="882" height="240" alt="image" src="https://github.com/user-attachments/assets/5dc9622a-4c83-419b-b29b-8809b49c3c4c" />


- **Partition the New Disk**
  ```bash
  sudo fdisk /dev/sdb
  ```
  
  Inside fdisk, do the following:
    - Press n → new partition
    - Press p → primary
    - Press 1 → partition number
    - Press Enter (accept defaults for first/last sector)
    - Press w → write changes
 <img width="1700" height="856" alt="image" src="https://github.com/user-attachments/assets/bbcc8341-bc8e-4d26-9b60-d6024462a6a3" />

- **Now check**
  ```bash
  lsblk
  ```
<img width="882" height="240" alt="lsblk" src="https://github.com/user-attachments/assets/5a0396b6-70a0-489a-9d95-cb13a8a62c38" />

- **Create Mount Point**
  ```bash
  sudo mkdir -p /mnt/mydisk
  ```
- **To mount:**
  ```bash
  sudo mount /dev/nvme1n1p1 /mnt/mydisk
  ```
 <img width="1498" height="718" alt="image" src="https://github.com/user-attachments/assets/3b68e80f-8bb0-432f-a7e9-47ddd682075f" />
- **To unmount:**
  ```bash
  sudo umount /mount/mydisk
  ```
  <img width="1382" height="576" alt="image" src="https://github.com/user-attachments/assets/f2e7b91a-9204-4711-b163-89fc4822678d" />

### 4.3 Configure Ulimit Settings
Ulimit is used to control how much system resources a user or process can use, such as open files, memory, or CPU.
#### 4.3.1 Check Current Ulimit Values
- For the current shell:
  ```bash
  ulimit -a
  ```
  Checks the maximum number of files a user or application is allowed to open at one time.
 <img width="1060" height="580" alt="image" src="https://github.com/user-attachments/assets/24b94de8-98f2-4f9f-a4ae-210b46c4e210" />

- For a specific limit (e.g., open files):
  ```bash
  ulimit -n
  ```
  Checks the maximum number of files a user or application is allowed to open at one time.
 <img width="990" height="66" alt="image" src="https://github.com/user-attachments/assets/97305095-9c85-4d3b-b249-eb79724e4ea1" />



#### 4.3.2 Set Temporary Ulimit for Current Session
```bash
ulimit -n 4096
```
Sets the limit so a user or application can open up to 4096 files at the same time.
<img width="1124" height="112" alt="image" src="https://github.com/user-attachments/assets/bbca3dfc-23b1-4727-a951-292094ada20d" />


- **Note:** This change lasts only for the current shell session.

#### 4.3.3 Configure Persistent Ulimits for Users

**Edit `/etc/security/limits.conf`:**
```bash
sudo nano /etc/security/limits.conf
```
- Add lines like:
  ```
  username   soft   nofile  4096
  username   hard   nofile  8192
  ```
  Or for all users:
  ```
  *   soft   nofile  4096
  *   hard   nofile  8192
  ```
- **Fields:**
  - *soft* - Soft limit (can be changed by the user up to the hard limit)
  - *hard* - Maximum limit (cannot be exceeded)

 ---  
## 5. Conclusion

Effective disk usage monitoring and proper ulimit configuration are essential for maintaining system stability and application reliability on Ubuntu systems. Regular disk checks help prevent storage-related issues such as disk exhaustion and inode shortages, which can lead to service outages if left unaddressed.

---
## 6. Contact Information

| Name             | Team                 | Contact Type | Details                                                             |
| ---------------- | -------------------- |------------ | ------------------------------------------------------------------- |
| Shreyas Awasthi | Saarthi              |Email        | [shreyas.awasthi.snaatak@mygurukulam.CO](mailto:shreyas.awasthi.snaatak@mygurukulam.CO) |


---
## 7. References

| Descriptions | Links |
|-------------|------|
| Ubuntu Server Guide – Disk Management | [Disk Management Guide](https://help.ubuntu.com/lts/serverguide/filesystems.html) |
| Ubuntu Documentation – limits.conf | [Limits.conf Manual](https://manpages.ubuntu.com/manpages/focal/en/man5/limits.conf.5.html) |
| Systemd Service Resource Limits | [Systemd Exec Documentation](https://www.freedesktop.org/software/systemd/man/systemd.exec.html#Process%20Properties) |

---

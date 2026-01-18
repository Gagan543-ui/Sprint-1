# Title: Disk Usage & Ulimit Configuration on Ubuntu OS

---

| Created By      | Created on   | Version | Last updated by   | Pre Reviewer   | L0 Reviewer | L1 Reviewer | L2 Reviewer |
|-----------------|--------------|---------|-------------------|----------------|-------------|-------------|-------------|
| Shreyas Awasthi  | 2026-01-16   | 1.0     | Shreyas Awasthi    |                |             |             |             |

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
   &nbsp;&nbsp;&nbsp;4.2.2. [Verify `/etc/fstab` for Persistent Mounts](#422-verify-etcfstab-for-persistent-mounts)  
   &nbsp;&nbsp;&nbsp;4.2.3. [Mount/Unmount Filesystems (if necessary)](#423-mountunmount-filesystems-if-necessary)  
   4.3. [Configure Ulimit Settings](#43-configure-ulimit-settings)  
   &nbsp;&nbsp;&nbsp;4.3.1. [Check Current Ulimit Values](#431-check-current-ulimit-values)  
   &nbsp;&nbsp;&nbsp;4.3.2. [Set Temporary Ulimit for Current Session](#432-set-temporary-ulimit-for-current-session)  
   &nbsp;&nbsp;&nbsp;4.3.3. [Configure Persistent Ulimits for Users](#433-configure-persistent-ulimits-for-users)  
   &nbsp;&nbsp;&nbsp;4.3.4. [Verify Effective Limits for a User/Process](#434-verify-effective-limits-for-a-userprocess)  
5. [Troubleshooting](#5-troubleshooting)
6. [References](#6-references)
7. [Revision History](#7-revision-history)

---

## 1. Purpose
This SOP outlines standardized procedures to:
- Check disk usage and mount points
- Configure and verify ulimit (user limits) settings for users and processes  
on Ubuntu-based systems, ensuring optimal system performance and resource usage.

---

## 2. Scope
Applicable to all Ubuntu servers.

---

## 3. Prerequisites
- Access to the Ubuntu server with sudo privileges.
- Basic knowledge of Linux command-line operations.

---

## 4. Procedure

### 4.1 Check Disk Usage

#### 4.1.1 List All Mounted Filesystems & Usage
```bash
df -hT
```
- **Purpose:** Displays all mounted filesystems with type and human-readable sizes.

<img width="1664" height="824" alt="image" src="https://github.com/user-attachments/assets/1d0a9b1c-96ec-4b28-9f2e-ae6fa100e320" />

- Ensure root (/) is not above 80% usage.

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
```bash
df -i
```
- **Purpose:** Identifies inode exhaustion, which can cause "disk full" errors despite free space.

<img width="1820" height="822" alt="image" src="https://github.com/user-attachments/assets/ec404ff7-1c86-4a6c-a278-f179803f49ea" />


---

### 4.2 Check and Manage Mount Points

#### 4.2.1 List Active Mounts
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


#### 4.2.3 Mount/Unmount Filesystems (if necessary)
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
  sudo mount /dev/sdXn /mount/point 
  ```
  <img width="1842" height="767" alt="Image" src="https://github.com/user-attachments/assets/bde1ee55-69c2-46a1-b885-1f92d6f81998" />

  
- **To unmount:**
  ```bash
  sudo umount /mount/point
  ```
  <img width="1818" height="636" alt="Image" src="https://github.com/user-attachments/assets/ddd1183b-db8a-4eb4-8d26-46a7ba88fd9a" />

---

### 4.3 Configure Ulimit Settings

#### 4.3.1 Check Current Ulimit Values
- For the current shell:
  ```bash
  ulimit -a
  ```
 <img width="1060" height="580" alt="image" src="https://github.com/user-attachments/assets/24b94de8-98f2-4f9f-a4ae-210b46c4e210" />

- For a specific limit (e.g., open files):
  ```bash
  ulimit -n
  ```
 <img width="990" height="66" alt="image" src="https://github.com/user-attachments/assets/97305095-9c85-4d3b-b249-eb79724e4ea1" />



#### 4.3.2 Set Temporary Ulimit for Current Session
```bash
ulimit -n 4096
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

**For systemd services:**
- Edit the service unit file or create a drop-in override:
  ```ini
  [Service]
  LimitNOFILE=8192
  ```
  Reload systemd and restart the service:
  ```bash
  sudo systemctl daemon-reload
  sudo systemctl restart <service-name>
  ```

#### 4.3.4 Verify Effective Limits for a User/Process
- After login or restart:
  ```bash
  ulimit -a
  ```
- For a running process (PID):
  ```bash
  cat /proc/<PID>/limits
  ```

---

## 5. Troubleshooting

| Issue                      | Possible Cause                | Solution                                      |
|----------------------------|-------------------------------|-----------------------------------------------|
| Disk appears full          | Large files, inode exhaustion | Use `du`, `df -i`, delete unnecessary files   |
| Ulimit not applied         | PAM misconfig, wrong user     | Check `/etc/security/limits.conf`, relogin    |
| Mount not persistent       | Missing `/etc/fstab` entry    | Update `/etc/fstab` and mount manually        |

---

## 6. References

- [Ubuntu Server Guide: Disk Management](https://help.ubuntu.com/lts/serverguide/filesystems.html)
- [Ubuntu: Limits.conf Documentation](https://manpages.ubuntu.com/manpages/focal/en/man5/limits.conf.5.html)
- [Systemd Service Limits](https://www.freedesktop.org/software/systemd/man/systemd.exec.html#Process%20Properties)

---

## 7. Revision History

| Version | Date       | Author        | Change Description       |
|---------|------------|---------------|-------------------------|
| 1.0     | 2026-01-18 | Shreyas AWasthi   | Initial version         |

---

**End of SOP**

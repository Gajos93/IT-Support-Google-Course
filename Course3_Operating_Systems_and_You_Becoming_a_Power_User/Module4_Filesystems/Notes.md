# 📂 Course 3 – Module 4: File Systems 🧭

## 🧩 Overview
In this module, we explore how **file systems** work in both **Windows** and **Linux**.  
You’ll learn how operating systems store, organize, manage, and protect data on disks.  
We cover directory structures, file system types, commands, metadata, and core concepts like inodes, journaling, fragmentation, and disk checking tools.

---

## 🗂️ What Is a File System?
A **file system** defines how data is stored, named, accessed, and organized on a storage device.

A file system manages:
- 📁 File and directory structure  
- 🧩 Metadata (permissions, ownership, timestamps)  
- 🔐 Access control  
- ♻️ Space allocation  
- 🧮 How files map to physical disk blocks  

---

## 🪟 Windows File Systems

### ⭐ Common Windows File Systems
- **NTFS (New Technology File System)**  
  - 🛡️ Supports permissions/ACLs  
  - 🔄 Journaling (prevents corruption)  
  - 🔐 Encryption (EFS)  
  - 📦 Large file support  
- **FAT32**  
  - 🗂️ Lightweight, universally compatible  
  - ⚠️ Max file size: 4 GB  
- **exFAT**  
  - 🧳 Ideal for USB/external drives  
  - ❗ No journaling  

### ⚙️ Useful Windows Commands
**View disk information:**  
`wmic logicaldisk get name,freespace,size`

**Check file system:**  
`fsutil fsinfo volumeinfo C:`

**Check disk health:**  
`chkdsk C: /f`

**List files:**  
`dir`

---

## 🐧 Linux File Systems

### ⭐ Common Linux File Systems
- **ext4** – stable, fast, journaling  
- **XFS** – excellent for large storage  
- **Btrfs** – snapshots, CoW, modern  
- **ext2/ext3** – older, less commonly used  

### 🗂️ Linux Directory Structure Overview
- `/` – root directory  
- `/home` – user home directories  
- `/etc` – configuration files  
- `/var` – logs and variable data  
- `/bin`, `/sbin` – essential system binaries  
- `/dev` – device files  
- `/mnt`, `/media` – mount points  

---

## 🧱 Core Concepts

### 📌 Inodes (Linux)
Store metadata:
- Ownership  
- Permissions  
- Timestamps  
- Disk block pointers  

📄 **Inodes do NOT store filenames** — directories map names to inode numbers.

### 📌 Journaling
Prevents corruption after crashes by logging changes before writing.

Used by: NTFS, ext3, ext4, XFS, Btrfs.

### 📌 Fragmentation
- Windows → fragmentation increases over time  
- Linux → minimal fragmentation due to allocation strategy  

### 📌 Mounting (Linux)
Linux mounts partitions into the directory tree.

Mount:  
`sudo mount /dev/sdb1 /mnt`

Unmount:  
`sudo umount /mnt`

---

## 📦 Disk & Partition Management (Linux)

**List disks:**  
`lsblk`  
`sudo fdisk -l`

**Create filesystem:**  
`sudo mkfs.ext4 /dev/sdb1`

**Check usage:**  
`df -h`

**Folder usage:**  
`du -sh /home/*`

**Repair filesystem:**  
`sudo fsck /dev/sdb1`

---

## 🪟 Disk & Volume Management (Windows)

**List volumes:**  
`Get-Volume`

**Format disk:**  
`Format-Volume -DriveLetter E -FileSystem NTFS`

**Check free space:**  
`Get-PSDrive`

**Disk Management GUI:**  
`diskmgmt.msc`

---

## 📁 File & Directory Commands

### 🐧 Linux
- `ls -l` – list files  
- `cp file1 file2` – copy  
- `mv file file2` – move/rename  
- `rm file.txt` – remove  
- `mkdir folder` – create directory  

### 🪟 Windows
- `dir` – list files  
- `copy file1 file2` – copy  
- `move file folder` – move  
- `del file.txt` – delete  
- `mkdir folder` – create directory  

---

## 🔐 Permissions & Ownership Recap

### Linux
- Change owner → `sudo chown user:group file`  
- Change permissions → `chmod 755 script.sh`  

### Windows NTFS
- View ACL → `icacls file.txt`  
- Grant → `icacls file.txt /grant username:F`  

---

## 💡 Key Takeaways
- File systems control how data is stored and accessed.  
- Windows uses NTFS/FAT32/exFAT, Linux uses ext4/XFS/Btrfs.  
- Linux uses mounting, Windows uses drive letters.  
- Inodes store metadata; journaling protects against corruption.  
- Tools like **fsck**, **chkdsk**, **lsblk**, **df**, and **diskmgmt.msc** support disk management.  

---

> 🧭 **Next Steps:**  
Learn to inspect metadata using `stat`, mount devices, and understand differences between file system behaviors.

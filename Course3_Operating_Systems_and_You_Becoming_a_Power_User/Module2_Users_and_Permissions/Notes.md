# 🧭 Course 3 – Module 2: Users and Permissions 🔐

## 🧩 Overview
In this module, we dive into managing **user accounts, groups, and file permissions** in both **Windows** and **Linux**. Understanding how to control access is fundamental to system security and administration. We'll cover creating users, organizing them into groups, and assigning appropriate rights based on the principle of least privilege.

---

## 👤 User Account Management

### 🪟 Managing Users in Windows
- Windows uses **Security Identifiers (SIDs)** to uniquely identify each user and group.
- Accounts can be **local** to the machine or part of a network **domain** (Active Directory).

**Types of Local Accounts:**
- 👑 **Administrator:** Has full control over the system.
- 👤 **Standard User:** Has limited privileges for daily tasks. This prevents accidental system-wide changes.
- 🚪 **Guest:** A highly restricted account for temporary access.

**Commands (PowerShell):**
| Task | PowerShell Command |
|------|--------------------|
| ➕ Create User | `New-LocalUser -Name "username" -Password $p` |
| 👀 View Users | `Get-LocalUser` |
| ✏️ Modify User | `Set-LocalUser -Name "username" -FullName "New Name"` |
| ❌ Remove User | `Remove-LocalUser -Name "username"` |
| 🔑 Set Password | `Set-LocalUser -Name "username" -Password $p` |

---

### 🐧 Managing Users in Linux
- Linux identifies users by a **User ID (UID)**. The **root** user (UID 0) has absolute administrative privileges.
- User information is stored in system files like `/etc/passwd` (user info) and `/etc/shadow` (passwords).

**Key Commands (Bash):**
| Task | Bash Command | Description |
|------|-----------------|-------------|
| ➕ Create User | `sudo useradd -m username` | The `-m` flag creates a home directory. |
| 🔑 Set Password | `sudo passwd username` | Sets or updates the user's password. |
| ✏️ Modify User | `sudo usermod -c "Comment" username` | The `-c` flag adds a descriptive comment. |
| ❌ Delete User | `sudo userdel -r username` | The `-r` flag removes the user's home directory and files. |
| 🔄 Switch User | `su username` or `sudo -u username -i` | Switches to another user's session. |

---

## 👥 Group Management
Groups simplify permission management by allowing you to assign rights to a collection of users at once, rather than one by one.

### 🪟 Groups in Windows
- 🛡️ **Administrators:** Members have full administrative control.
- 👥 **Users:** Standard, everyday users with limited rights.
- 🖥️ **Remote Desktop Users:** Members can connect to the computer remotely.

**Commands (PowerShell):**
| Task | PowerShell Command |
|------|--------------------|
| ➕ Create Group | `New-LocalGroup -Name "groupname"` |
| ➡️ Add User to Group | `Add-LocalGroupMember -Group "groupname" -Member "username"` |
| 👀 View Group Members | `Get-LocalGroupMember -Group "groupname"` |
| ⬅️ Remove User from Group | `Remove-LocalGroupMember -Group "groupname" -Member "username"` |
| ❌ Delete Group | `Remove-LocalGroup -Name "groupname"` |

---

### 🐧 Groups in Linux
- Each user belongs to a **primary group**. They can also be members of multiple **secondary groups**.
- Group information is stored in the `/etc/group` file.

**Key Commands (Bash):**
| Task | Bash Command | Description |
|------|-----------------|-------------|
| ➕ Create Group | `sudo groupadd groupname` | Creates a new group. |
| ➡️ Add User to Group | `sudo usermod -aG groupname username` | The `-aG` flags append the user to a secondary group. |
| 👀 View a User's Groups | `groups username` or `id username` | Shows the user's primary and secondary groups. |
| ❌ Delete Group | `sudo groupdel groupname` | Removes an empty group. |
| 🔄 Change a File's Group | `sudo chgrp groupname file.txt` | Changes the group ownership of a file. |

---

## 🔑 File and Folder Permissions

### 🪟 Windows NTFS Permissions
- Permissions are managed using **Access Control Lists (ACLs)**.
- Each ACL contains **Access Control Entries (ACEs)** that specify a user or group and their level of access.

**Common NTFS Permissions:**
- 👑 **Full Control:** Allows reading, writing, modifying, deleting, and changing permissions.
- ✏️ **Modify:** Allows reading, writing, executing, and deleting.
- 📖 **Read & Execute:** Allows viewing files and running executables.
- ✍️ **Write:** Allows creating new files and modifying existing ones.
- 👀 **Read:** Allows viewing file contents and properties.

**🛠️ Tools:**
- **GUI:** The **Security** tab in a file or folder's **Properties** dialog.
- **CLI (CMD):** `icacls` (Example: `icacls file.txt /grant "username":F`)
- **CLI (PowerShell):** `Get-Acl` and `Set-Acl`

---

### 🐧 Linux Permissions
- A simpler model based on three sets of permissions for three types of identities.

**Identities:**
- 👤 **User (u):** The owner of the file.
- 👥 **Group (g):** The group that the file belongs to.
- 🌐 **Other (o):** All other users on the system.

**Permissions:**
- 📖 **Read (r):** Numeric value `4`. View file contents or list directory contents.
- ✍️ **Write (w):** Numeric value `2`. Modify a file or create/delete files within a directory.
- 🏃 **Execute (x):** Numeric value `1`. Run a file as a script or enter a directory.

**Commands:**
| Command | Example | Description |
|---------|---------|-------------|
| `chmod` | `chmod 755 script.sh` | Changes permissions using octal (numeric) mode. `7` (rwx), `5` (r-x). |
| `chmod` | `chmod u+x script.sh` | Changes permissions using symbolic mode (adds execute for the user). |
| `chown` | `chown username:groupname file` | Changes both the owner and group of a file simultaneously. |
| `ls -l` | `ls -l file.txt` | Displays permissions in the format `-rwxr-xr--`. |

---

## 🛡️ Administrative Privileges & Escalation

### 🪟 Windows: User Account Control (UAC)
- **UAC** is a security feature that helps prevent unauthorized changes to the system.
- When an action requires administrative rights, UAC prompts the user for confirmation or an administrator's password.
- You can run a program with elevated rights by right-clicking it and selecting **Run as administrator**.

### 🐧 Linux: `sudo` and `su`
- Adheres to the **principle of least privilege**, where you use a regular account and only escalate privileges when needed.
- **`sudo` (Superuser Do):** Executes a single command with root privileges. This is the preferred method for administrative tasks.
  - Example: `sudo apt update`
- **`su` (Switch User):** Switches to the `root` user's shell, giving you a persistent administrative session. It is considered less secure for general use than `sudo`.
  - Example: `su -` (switches to the root user and loads its environment)

---

### 💡 Key Takeaways
- Always follow the **principle of least privilege** by granting users only the permissions they need to perform their jobs.
- **Groups** are the most efficient way to manage permissions for multiple users.
- Windows uses a granular **ACL-based model**, while Linux uses a simpler **user/group/other** model.
- Use **`sudo`** in Linux and respond to **UAC** prompts in Windows to perform administrative tasks securely without being logged in as the highest-level administrator.
- Mastering user and permission management is crucial for maintaining a secure and organized IT environment.

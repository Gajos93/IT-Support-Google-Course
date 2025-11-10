#  🧭 Course 3 – Module 2: Users and Permissions 🔐

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
| :-- | :-- |
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
| :-- | :-- | :-- |
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
| :-- | :-- |
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
| :-- | :-- | :-- |
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
- 📖 **Read \& Execute:** Allows viewing files and running executables.
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
| :-- | :-- | :-- |
| `chmod` | `chmod 755 script.sh` | Changes permissions using octal (numeric) mode. `7` (rwx), `5` (r-x). |
| `chmod` | `chmod u+x script.sh` | Changes permissions using symbolic mode (adds execute for the user). |
| `chown` | `chown username:groupname file` | Changes both the owner and group of a file simultaneously. |
| `ls -l` | `ls -l file.txt` | Displays permissions in the format `-rwxr-xr--`. |


---

## 🛡️ Administrative Privileges \& Escalation

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
- Mastering user and permission management is crucial for maintaining a secure and organized IT environment. Oto szablon

Of course. Based on the template you provided, here are the notes for "Module 2: Users and Permissions" in Markdown format.

# 🧭 Course 3 – Module 2: Users and Permissions 🔐

## 🧩 Overview

This module explores the management of **user accounts, groups, and file permissions** in both **Windows** and **Linux**. Mastering access control is a critical aspect of system security and administration. The topics covered include creating users, organizing them into groups, and assigning permissions based on the principle of least privilege.[^3][^4]

***

## 👤 User Account Management

### 🪟 Managing Users in Windows

- Windows uses **Security Identifiers (SIDs)** to give each user and group a unique identity.[^4]
- Accounts can be either **local** to the machine or part of a network **domain** through Active Directory.[^3]

**Types of Local Accounts:**

- 👑 **Administrator:** Possesses complete control over the system.[^3]
- 👤 **Standard User:** Has restricted privileges for everyday operations, which helps to prevent unintentional system-wide modifications.[^3]
- 🚪 **Guest:** A highly limited account designed for temporary access.

**Commands (PowerShell):**


| Task | PowerShell Command |
| :-- | :-- |
| ➕ Create User | `New-LocalUser -Name "username" -Password $p` |
| 👀 View Users | `Get-LocalUser` |
| ✏️ Modify User | `Set-LocalUser -Name "username" -FullName "New Name"` |
| ❌ Remove User | `Remove-LocalUser -Name "username"` |
| 🔑 Set Password | `Set-LocalUser -Name "username" -Password $p` |


***

### 🐧 Managing Users in Linux

- Linux identifies users with a **User ID (UID)**, and the **root** user (UID 0) holds absolute administrative power.[^3]
- User information is stored in system files such as `/etc/passwd` for user details and `/etc/shadow` for passwords.[^3]

**Key Commands (Bash):**


| Task | Bash Command | Description |
| :-- | :-- | :-- |
| ➕ Create User | `sudo useradd -m username` | The `-m` flag ensures a home directory is created. |
| 🔑 Set Password | `sudo passwd username` | This command sets or updates a user's password. |
| ✏️ Modify User | `sudo usermod -c "Comment" username` | The `-c` flag is used to add a descriptive comment. |
| ❌ Delete User | `sudo userdel -r username` | The `-r` flag removes the user's home directory and associated files [^3]. |
| 🔄 Switch User | `su username` or `sudo -u username -i` | This command switches to another user's session. |


***

## 👥 Group Management

Groups make permission management more efficient by allowing you to assign rights to a set of users simultaneously, rather than individually.[^5]

### 🪟 Groups in Windows

- 🛡️ **Administrators:** Members of this group have full administrative control.[^3]
- 👥 **Users:** These are standard users with limited privileges.[^3]
- 🖥️ **Remote Desktop Users:** Members can establish a remote connection to the computer.

**Commands (PowerShell):**


| Task | PowerShell Command |
| :-- | :-- |
| ➕ Create Group | `New-LocalGroup -Name "groupname"` |
| ➡️ Add User to Group | `Add-LocalGroupMember -Group "groupname" -Member "username"` |
| 👀 View Group Members | `Get-LocalGroupMember -Group "groupname"` |
| ⬅️ Remove User from Group | `Remove-LocalGroupMember -Group "groupname" -Member "username"` |
| ❌ Delete Group | `Remove-LocalGroup -Name "groupname"` |


***

### 🐧 Groups in Linux

- Every user is part of a **primary group** and can also belong to multiple **secondary groups** [].
- Information about groups is stored in the `/etc/group` file.[^3]

**Key Commands (Bash):**


| Task | Bash Command | Description |
| :-- | :-- | :-- |
| ➕ Create Group | `sudo groupadd groupname` | This command creates a new group. |
| ➡️ Add User to Group | `sudo usermod -aG groupname username` | The `-aG` flags add the user to a secondary group without removing them from others. |
| 👀 View a User's Groups | `groups username` or `id username` | These commands display a user's primary and secondary groups. |
| ❌ Delete Group | `sudo groupdel groupname` | This removes a group, which must be empty. |
| 🔄 Change a File's Group | `sudo chgrp groupname file.txt` | This command changes the group ownership of a file. |


***

## 🔑 File and Folder Permissions

### 🪟 Windows NTFS Permissions

- Permissions are controlled via **Access Control Lists (ACLs)**.[^4]
- Each ACL is composed of **Access Control Entries (ACEs)** that define a user or group's access level.[^4]

**Common NTFS Permissions:**

- 👑 **Full Control:** Grants permission to read, write, modify, delete, and alter permissions.
- ✏️ **Modify:** Allows for reading, writing, executing, and deleting.
- 📖 **Read \& Execute:** Grants permission to view files and run executables.
- ✍️ **Write:** Allows for the creation of new files and modification of existing ones.
- 👀 **Read:** Grants permission to view file contents and their properties.

**🛠️ Tools:**

- **GUI:** The **Security** tab within a file or folder's **Properties** dialog.
- **CLI (CMD):** `icacls` (e.g., `icacls file.txt /grant "username":F`)
- **CLI (PowerShell):** `Get-Acl` and `Set-Acl`

***

### 🐧 Linux Permissions

- Linux uses a simpler model based on three sets of permissions for three identity types.[^4]

**Identities:**

- 👤 **User (u):** The file's owner.
- 👥 **Group (g):** The group associated with the file.
- 🌐 **Other (o):** All other users on the system.

**Permissions:**

- 📖 **Read (r):** Has a numeric value of `4` and allows viewing file contents or listing directory contents.
- ✍️ **Write (w):** Has a numeric value of `2` and allows modifying a file or managing files within a directory.
- 🏃 **Execute (x):** Has a numeric value of `1` and allows running a file as a script or entering a directory.

**Commands:**


| Command | Example | Description |
| :-- | :-- | :-- |
| `chmod` | `chmod 755 script.sh` | This command changes permissions using octal (numeric) mode, where `7` is rwx and `5` is r-x. |
| `chmod` | `chmod u+x script.sh` | This command alters permissions using symbolic mode, in this case adding execute permission for the user. |
| `chown` | `chown username:groupname file` | This command changes both the owner and group of a file at the same time. |
| `ls -l` | `ls -l file.txt` | This command shows permissions in the format `-rwxr-xr--`. |


***

## 🛡️ Administrative Privileges \& Escalation

### 🪟 Windows: User Account Control (UAC)

- **UAC** is a security feature designed to prevent unauthorized system changes.[^1][^4]
- When an action requires administrative rights, UAC will prompt the user for confirmation or an administrator's password.[^4]
- To run a program with elevated privileges, you can right-click it and choose **Run as administrator**.


### 🐧 Linux: `sudo` and `su`

- Linux follows the **principle of least privilege**, meaning you should use a standard account and only elevate privileges when necessary.[^4]
- **`sudo` (Superuser Do):** Executes a single command with root privileges and is the recommended method for administrative tasks.[^3]
    - Example: `sudo apt update`
- **`su` (Switch User):** Switches to the `root` user's shell, creating a persistent administrative session. It is generally considered less secure than `sudo` for routine use.[^3]
    - Example: `su -` (switches to the root user and loads its environment).

***

### 💡 Key Takeaways

- Always adhere to the **principle of least privilege** by giving users only the permissions essential for their tasks.[^4]
- Using **groups** is the most effective method for managing permissions for multiple users.[^5]
- Windows employs a detailed **ACL-based model**, whereas Linux utilizes a more straightforward **user/group/other** model.[^4]
- Use **`sudo`** in Linux and respond to **UAC** prompts in Windows to carry out administrative tasks securely without being logged in as the highest-level administrator.[^4]
- A thorough understanding of user and permission management is essential for maintaining a secure and well-organized IT environment.[^5]
<span style="display:none">[^2]</span>

<div align="center">⁂</div>


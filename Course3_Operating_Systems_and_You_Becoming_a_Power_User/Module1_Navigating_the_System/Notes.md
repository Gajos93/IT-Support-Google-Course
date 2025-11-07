# 🧭 Course 3 – Module 1: Navigating the System

## 🧩 Overview
In this module, we learn how to **navigate and interact with operating systems** using both the **Graphical User Interface (GUI)** and the **Command-Line Interface (CLI)**.  
We explore file systems, directories, paths, and essential commands in both **Windows PowerShell** and **Linux Bash**.

---

## 💻 Interfaces: GUI vs CLI

### 🖱️ Graphical User Interface (GUI)
- GUI provides **visual interaction** with windows, icons, and menus.
- Easier for beginners but less efficient for automation or scripting.
- Common GUIs:
  - **Windows Explorer**
  - **macOS Finder**
  - **GNOME / KDE (Linux)**

### 💡 Advantages
- Intuitive and user-friendly.
- Minimal command memorization.
- Ideal for managing files and applications interactively.

---

### 💻 Command-Line Interface (CLI)
- Text-based interface for **direct system control**.
- Faster, more powerful, and scriptable.
- Requires learning commands and syntax.

**Examples:**
- **Windows:** PowerShell or Command Prompt (`cmd`)
- **Linux:** Bash (Bourne Again Shell), Zsh, etc.

**Why CLI matters:**
- Easier to **automate** repetitive tasks.
- Enables **remote system management**.
- Provides **greater control and feedback** than GUI.

---

## 📁 Understanding File Systems

### 🔹 Structure
- File systems organize how data is stored and accessed.
- Everything is represented as **files and directories (folders)**.

### 🪟 Windows File System
- Hierarchical structure with **drive letters** (`C:\`, `D:\`).
- Uses **backslashes** (`\`) for paths.
  - Example: `C:\Users\John\Documents\file.txt`

### 🐧 Linux File System
- Single-root structure — everything starts from `/`
- Uses **forward slashes** (`/`) for paths.
  - Example: `/home/john/documents/file.txt`

**Common Directories in Linux:**
| Directory | Purpose |
|------------|----------|
| `/` | Root directory |
| `/home` | User home directories |
| `/etc` | Configuration files |
| `/var` | Variable data (logs, mail) |
| `/usr` | User programs and libraries |
| `/tmp` | Temporary files |
| `/bin`, `/sbin` | Essential system binaries |

---

## 🚀 Navigating with the Command Line

### 🔹 Basic Commands (Windows PowerShell vs Linux Bash)

| Task | Windows PowerShell | Linux Bash | Description |
|------|--------------------|-------------|--------------|
| Show current directory | `pwd` | `pwd` | Print working directory |
| List files | `dir` | `ls` | Display contents of a directory |
| Change directory | `cd folder` | `cd folder` | Move between directories |
| Go back one directory | `cd ..` | `cd ..` | Go up one level |
| Create directory | `mkdir folder` | `mkdir folder` | Create new folder |
| Remove directory | `rmdir folder` | `rmdir folder` | Remove empty folder |
| Copy file | `copy file1 file2` | `cp file1 file2` | Copy file |
| Move file | `move file1 folder` | `mv file1 folder` | Move or rename file |
| Delete file | `del file.txt` | `rm file.txt` | Delete file |
| Display text file | `type file.txt` | `cat file.txt` | View contents of file |
| Clear screen | `cls` | `clear` | Clear terminal screen |

---

### 🔹 Paths: Absolute vs Relative
- **Absolute path:** Full path from the root directory.
  - Example: `/home/user/file.txt` or `C:\Users\User\file.txt`
- **Relative path:** Relative to current working directory.
  - Example: `../Documents/file.txt`

**Tips:**
- `.` = current directory  
- `..` = parent directory  

---

## 🔎 Viewing and Managing Files

### 🔹 Viewing Files
- **Windows:** `type filename.txt`
- **Linux:** `cat filename.txt` or `less filename.txt`

### 🔹 Creating and Editing Files
| Action | Windows | Linux |
|--------|----------|--------|
| Create file | `echo "text" > file.txt` | `touch file.txt` |
| Append to file | `echo "text" >> file.txt` | `echo "text" >> file.txt` |
| Edit file | Use Notepad or PowerShell ISE | Use `nano`, `vim`, or `gedit` |

---

## 🧠 PowerShell Basics (Windows)

PowerShell is an advanced shell with scripting and automation capabilities.

### 🔹 Cmdlets
- **Cmdlets** are small, single-function commands.
- Always use the pattern:  
  `Verb-Noun` → Example: `Get-Process`, `Set-Date`, `Restart-Computer`

**Common PowerShell Cmdlets:**
| Task | Command |
|------|----------|
| Show all commands | `Get-Command` |
| Get help | `Get-Help` |
| List files | `Get-ChildItem` |
| Display processes | `Get-Process` |
| Stop process | `Stop-Process -Name notepad` |
| Show system info | `Get-ComputerInfo` |

**Aliases:**  
PowerShell supports Unix-like aliases for convenience:
| Alias | Equivalent Cmdlet |
|--------|--------------------|
| `ls` | `Get-ChildItem` |
| `cd` | `Set-Location` |
| `cp` | `Copy-Item` |
| `mv` | `Move-Item` |
| `rm` | `Remove-Item` |

---

## 🐧 Bash Basics (Linux)

### 🔹 Common Commands
| Task | Command | Description |
|------|----------|-------------|
| Show current user | `whoami` | Display logged-in user |
| Show date and time | `date` | Print system date/time |
| View running processes | `ps`, `top` | Display active processes |
| Display current directory | `pwd` | Print working directory |
| Change permissions | `chmod 755 file` | Modify access rights |
| Change ownership | `chown user file` | Change file owner |
| Search text | `grep "word" file.txt` | Search patterns in files |
| View disk usage | `df -h`, `du -h` | Display storage info |
| Show system info | `uname -a` | Kernel and system info |

---

## ⚙️ Environment Variables

Environment variables store information about the system and user environment.

### 🔹 Examples:
| OS | Command | Example Variable | Description |
|----|----------|------------------|--------------|
| Windows | `$env:PATH` | `PATH` | Directories where system searches for executables |
| Linux | `echo $PATH` | `PATH` | Same purpose on Linux |
| Linux | `export VAR=value` | `export EDITOR=vim` | Set environment variable |

---

## 🔐 Permissions Overview (Linux)

- Every file has **permissions** for:
  - **User (u)** – owner  
  - **Group (g)** – group members  
  - **Others (o)** – everyone else

**Example:** `-rw-r--r--`  
- `r` = read, `w` = write, `x` = execute  
- Change permissions with `chmod`  
  - Example: `chmod 755 script.sh`

---

## 🧩 Practical CLI Skills

### 🔹 Redirecting Output
- `>` → redirect output to a new file.  
- `>>` → append output to an existing file.  
- `|` → send output of one command to another (pipe).  

**Examples:**
bash
ls > files.txt
cat file.txt | grep "error"

### Combining Commands

| Operator | Description |
|----------|-------------|
| `&&` | Run next command **only if previous succeeded** |
| `;` | Run multiple commands **sequentially**, regardless of success |
| `|` | **Pipe** output of one command into another |

---

### Useful Shortcuts

| Shortcut | Function |
|----------|-----------|
| `Ctrl + C` | Stop current command |
| `Ctrl + L` | Clear screen |
| `Ctrl + A` | Go to start of line |
| `Ctrl + E` | Go to end of line |
| `↑ / ↓` | Browse command history |
| `Tab` | Auto-complete command or filename |

---

### Key Takeaways

- The **CLI** gives deeper control and flexibility than GUI.  
- **PowerShell and Bash** share similar concepts but use different syntax.  
- Understanding **paths, permissions, and environment variables** is essential for any IT Support role.  
- Practice using both systems — mastering CLI is a defining skill of a power user.  
- Combine **GUI and CLI tools** to work faster and troubleshoot more effectively.

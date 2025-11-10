# 📦 Course 3 – Module 3: Package and Software Management 🧰

## 🧩 Overview
In this module, we explore how **software is installed, updated, and managed** across **Windows** and **Linux** systems. Understanding how package managers work allows system administrators and power users to maintain system stability, security, and efficiency.  

We'll look at how both systems handle software dependencies, repositories, and command-line tools for installing and maintaining packages.

---

## 🐧 Linux Package Management

Linux distributions use **package managers** to automate the process of installing, updating, and removing software.  
Each package includes:
- The application or program files.
- **Metadata** (information about the package).
- **Dependencies** (other packages required to make it work).

---

### 📦 Types of Package Managers

| Package Manager | Distribution | Command Example | Description |
|-----------------|---------------|-----------------|--------------|
| `dpkg` | Debian / Ubuntu | `sudo dpkg -i package.deb` | The low-level tool for installing `.deb` packages. |
| `apt` | Debian / Ubuntu | `sudo apt install package` | A higher-level tool built on top of `dpkg` that handles dependencies automatically. |
| `yum` | CentOS / RHEL | `sudo yum install package` | Used in older Red Hat–based systems for package management. |
| `dnf` | Fedora / RHEL 8+ | `sudo dnf install package` | The modern replacement for `yum`. |
| `snap` | Ubuntu / cross-distro | `sudo snap install package` | Uses containerized software packages. |
| `flatpak` | Cross-distro | `flatpak install app` | Another universal package format, independent of system libraries. |

---

### ⚙️ Common `apt` Commands

| Task | Command | Description |
|------|----------|-------------|
| 🔍 Search for a package | `apt search package` | Lists available packages matching the search term. |
| 📥 Install a package | `sudo apt install package` | Downloads and installs the specified package. |
| ❌ Remove a package | `sudo apt remove package` | Removes a package while keeping configuration files. |
| 🧹 Remove completely | `sudo apt purge package` | Removes a package and its configuration files. |
| ♻️ Update package list | `sudo apt update` | Updates the local list of available packages. |
| ⬆️ Upgrade all packages | `sudo apt upgrade` | Installs available updates for all installed packages. |
| 🧰 Fix broken dependencies | `sudo apt --fix-broken install` | Repairs missing dependencies or partial installs. |

---

### 🧩 Repository Management
Linux systems use **software repositories**, which are online servers hosting packages.

- 🗂️ Repository info is stored in `/etc/apt/sources.list` or in files under `/etc/apt/sources.list.d/`.
- To **add a repository**, use:
  ```bash
  sudo add-apt-repository ppa:repository-name
  ```
- To **update the package list** after adding or removing repositories:
  ```bash
  sudo apt update
  ```

Repositories ensure software authenticity and version control through **GPG signatures**.

---

## 🪟 Windows Software Management

Unlike Linux, Windows software can come from multiple sources — **manual installers**, **MSI packages**, or **package managers** like **winget** and **Chocolatey**.

---

### 💾 Software Installation Methods

| Method | Example | Description |
|--------|----------|-------------|
| 🖱️ `.exe` installers | `setup.exe` | Common graphical installers that walk you through installation steps. |
| 🧩 `.msi` packages | `app.msi` | Microsoft Installer files that allow standardized, automated installations. |
| 🧰 Package managers | `winget install app` | Command-line tools for installing apps from trusted repositories. |

---

### ⚙️ Windows Package Managers

| Tool | Description | Example Command |
|------|--------------|----------------|
| **Winget** | Built-in Windows package manager (since Windows 10 2004+). | `winget install notepad++` |
| **Chocolatey** | Popular community package manager using PowerShell and NuGet. | `choco install googlechrome` |
| **Microsoft Store** | GUI-based software source for trusted apps. | Access via Start Menu → Microsoft Store |

Package managers help automate installation and ensure consistency across systems — especially useful for administrators managing multiple computers.

---

### 🧠 Useful `winget` Commands

| Task | Command | Description |
|------|----------|-------------|
| 🔍 Search for an app | `winget search appname` | Finds applications available in repositories. |
| 📥 Install an app | `winget install appname` | Installs the specified app. |
| ⬆️ Upgrade installed apps | `winget upgrade --all` | Updates all installed software packages. |
| ❌ Uninstall an app | `winget uninstall appname` | Removes the specified application. |
| 📋 List installed packages | `winget list` | Displays installed software with version details. |

---

## 🧰 Managing Software Updates

Keeping software up to date is critical for **security, stability, and performance**.

- Linux systems often use **automated background updates** or manual commands (`apt upgrade`).
- Windows handles updates through **Windows Update**, but third-party apps may need manual updates or package manager automation.

**Pro Tip:**  
Use scheduled update tasks or scripts to regularly check for and install updates.

---

## 🧼 Removing and Cleaning Packages

Over time, unused packages and dependencies can consume space.

### 🐧 Linux
```bash
sudo apt autoremove
sudo apt clean
```
- `autoremove`: Removes dependencies that are no longer required.
- `clean`: Clears the package cache.

### 🪟 Windows
- Use `winget uninstall appname` or **Apps & Features** in the Control Panel.
- Chocolatey also supports cleanup commands:
  ```powershell
  choco uninstall packagename
  ```

---

## 💡 Key Takeaways

- Linux uses **package managers** like `apt`, `yum`, and `dnf` to automate software management.  
- Windows increasingly supports **CLI package management** with **winget** and **Chocolatey**.  
- Always keep your software **updated** to protect against security vulnerabilities.  
- Use **repositories** or **trusted sources** — never download random executables from unverified websites.  
- Understanding package management helps maintain a **secure, efficient, and consistent computing environment** across multiple systems.

---

> 🧭 **Next Steps:**  
> Experiment with installing, updating, and removing software using both GUI and CLI tools.  
> Compare how dependencies and updates are handled differently between Windows and Linux!

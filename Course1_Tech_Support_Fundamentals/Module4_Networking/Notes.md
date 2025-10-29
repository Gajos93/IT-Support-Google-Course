# 🌐 Course 1 – Module 4: Networking

## 📝 Notes

### 🔹 What is Networking?
- **Networking** 🌍 – connecting computers and devices to share data and resources.  
- Two main types of networks:  
  - **LAN (Local Area Network)** 🏠 – small, local (home, office).  
  - **WAN (Wide Area Network)** 🌍 – larger scale, connects multiple LANs (e.g., the Internet).  

---

### 🔹 Addressing
- **IP Address** 🔢 – unique identifier for each device.  
  - **IPv4** 📄 – 32-bit address, written as 4 decimal numbers (e.g., 192.168.1.1).  
  - **IPv6** 🆕 – 128-bit address, created to solve IPv4 exhaustion.  
- **MAC Address** 🖥️ – physical identifier assigned to a network card.  
- **Subnetting** ➗ – dividing a network into smaller parts for efficiency and security.  
- **Default Gateway** 🚪 – the router that connects a LAN to the outside world.  

---

### 🔹 Core Services
- **DNS (Domain Name System)** 📖 – translates domain names (e.g., `google.com`) into IP addresses.  
- **DHCP (Dynamic Host Configuration Protocol)** 🎛️ – automatically assigns IP, mask, gateway, and DNS.  
- **NAT (Network Address Translation)** 🔄 – allows multiple private IPs to share one public IP.  

---

### 🔹 Protocols
- **TCP (Transmission Control Protocol)** 📦 – reliable, connection-oriented, ensures correct order.  
- **UDP (User Datagram Protocol)** ⚡ – fast, connectionless, less reliable (streaming, gaming).  
- **HTTP/HTTPS** 🌍 – web browsing protocols (HTTPS = encrypted).  
- **FTP (File Transfer Protocol)** 📂 – transferring files.  
- **SMTP/IMAP/POP3** ✉️ – email protocols (sending/receiving mail).  

---

### 🔹 Tools & Commands
- **ping** 🏓 – checks connectivity between devices.  
- **tracert / traceroute** 🧭 – shows the path packets take to a destination.  
- **nslookup / dig** 🔎 – tests DNS resolution.  
- **ipconfig / ifconfig** ⚙️ – shows network configuration.  
- **netstat / ss** 📊 – displays active connections and ports.  
- **arp -a** 📒 – shows mapping of IP ↔ MAC in local network.  

---

### 🔹 Troubleshooting Workflow
1. **ping 127.0.0.1** 💻 – test local TCP/IP stack.  
2. **ping Gateway (e.g., 192.168.1.1)** 🚪 – test LAN connectivity.  
3. **ping 8.8.8.8** 🌍 – test Internet connectivity by IP.  
4. **ping google.com** 📖 – test DNS resolution.  

Common issues:
- ❌ **No Internet** → check cables, Wi-Fi, gateway.  
- ⚠️ **Wrong IP configuration** → renew DHCP lease.  
- 🌀 **DNS issues** → try another DNS (8.8.8.8, 1.1.1.1).  
- 🐢 **Slow network** → check interference, bandwidth, devices.  

---

## 📖 Key Terms

- **Networking** 🌍 – practice of connecting devices to share data/resources.  
- **LAN (Local Area Network)** 🏠 – local network (home/office).  
- **WAN (Wide Area Network)** 🌍 – large-scale network (Internet).  
- **IP Address** 🔢 – unique identifier for a device.  
- **IPv4** 📄 – 32-bit addressing system.  
- **IPv6** 🆕 – 128-bit addressing system.  
- **MAC Address** 🖥️ – hardware identifier for a NIC.  
- **Subnetting** ➗ – dividing networks into smaller subnets.  
- **Default Gateway** 🚪 – router connecting LAN to external networks.  
- **DNS (Domain Name System)** 📖 – resolves names into IPs.  
- **DHCP** 🎛️ – assigns IP addresses automatically.  
- **NAT (Network Address Translation)** 🔄 – maps private IPs to a public IP.  
- **TCP (Transmission Control Protocol)** 📦 – reliable, ordered communication.  
- **UDP (User Datagram Protocol)** ⚡ – fast, no delivery guarantee.  
- **HTTP/HTTPS** 🌍 – protocols for web browsing.  
- **FTP** 📂 – file transfer protocol.  
- **SMTP/IMAP/POP3** ✉️ – email protocols.  
- **ping** 🏓 – connectivity testing tool.  
- **tracert / traceroute** 🧭 – shows packet route.  
- **nslookup / dig** 🔎 – DNS testing tools.  
- **ipconfig / ifconfig** ⚙️ – displays network settings.  
- **netstat / ss** 📊 – shows active connections/ports.  
- **arp -a** 📒 – shows IP ↔ MAC table.  
- **ICMP (Internet Control Message Protocol)** 📡 – protocol used by ping/traceroute.  

---

## 💡 Insights
- Networking underpins everything in IT – without it, no system can communicate.  
- Addressing and DNS are crucial – many problems trace back to these layers.  
- The **ping sequence (local → gateway → Internet → DNS)** is the fastest way to locate connectivity issues.  
- Knowing **protocols and ports** is essential for troubleshooting applications.  

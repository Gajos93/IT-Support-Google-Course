# 📖 Networking – Terminology Cheat Sheet

## 🌐 Network Basics
- **LAN (Local Area Network)** 🏠 – a small local network (home, office).  
- **WAN (Wide Area Network)** 🌍 – a large network that connects multiple LANs (the Internet).  
- **Packet** 📦 – the smallest unit of data transmitted across a network.  

---

## 🔢 Addressing
- **IP Address** 🔢 – a unique number that identifies a device on a network.  
  - **IPv4** 📄 – 32-bit address, e.g. `192.168.1.1`.  
  - **IPv6** 🆕 – 128-bit address, e.g. `2001:db8::1`.  
- **MAC Address** 🖥️ – physical hardware address of a network interface card (unique per device).  
- **Subnet Mask / CIDR** ➗ – defines the network portion and host portion of an IP address.  
- **Default Gateway** 🚪 – the router that connects a LAN to external networks (e.g., the Internet).  

---

## 🌐 Core Services
- **DNS (Domain Name System)** 📖 – translates domain names (e.g. `google.com`) into IP addresses.  
- **DHCP (Dynamic Host Configuration Protocol)** 🎛️ – automatically assigns IP addresses, subnet mask, gateway, and DNS to devices.  
- **NAT (Network Address Translation)** 🔄 – translates private LAN IP addresses into a public IP address.  

---

## 📡 Protocols
- **TCP (Transmission Control Protocol)** 📦 – reliable, ordered, connection-oriented (used for web, email, file transfer).  
- **UDP (User Datagram Protocol)** ⚡ – fast, connectionless, no delivery guarantee (used for streaming, VoIP, gaming).  
- **HTTP/HTTPS** 🌍 – web browsing protocols (HTTPS = secure, encrypted).  
- **FTP (File Transfer Protocol)** 📂 – protocol for transferring files.  
- **SMTP/IMAP/POP3** ✉️ – email protocols: sending (SMTP) and receiving (IMAP, POP3).  

---

## 🛠️ Tools & Commands
- **ping** 🏓 – checks connectivity with another device (ICMP Echo).  
- **tracert / traceroute** 🧭 – shows the path packets take across routers.  
- **nslookup / dig** 🔎 – tests DNS resolution (domain name → IP address).  
- **ipconfig (Windows) / ifconfig (Linux)** ⚙️ – shows network configuration details.  
- **netstat / ss** 📊 – displays active connections and listening ports.  
- **arp -a** 📒 – shows IP ↔ MAC address mappings in the local network.  

---

## 🚧 Troubleshooting Steps
1. **ping 127.0.0.1** 💻 – tests the TCP/IP stack locally.  
2. **ping Gateway (e.g. 192.168.1.1)** 🚪 – tests connection to the local router.  
3. **ping 8.8.8.8** 🌍 – tests if the Internet is reachable by IP.  
4. **ping google.com** 📖 – tests if DNS resolution works.  

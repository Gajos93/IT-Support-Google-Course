# 🛰️ Course 2 – Module 2: The Network Layer

## 📝 Notes

### 🔹 Role of the Network Layer
- The **Network Layer** (Layer 3 OSI) is responsible for:
  - **Logical addressing** 🔢 – assigning IP addresses to devices.  
  - **Routing** 🛣️ – choosing the best path to a destination.  
  - **Forwarding** 📦 – moving packets between networks hop by hop.  
- Without it, communication would be limited to the same local link (LAN).

---

### 🔹 IPv4 Addresses
- **IPv4** = 32-bit address written in 4 octets (e.g., `192.168.1.25`).  
- Each octet ranges **0–255**.  
- Address structure:  
  - **Network ID** 🌐 – identifies the network/subnet.  
  - **Host ID** 💻 – identifies a device in that subnet.  

**Address types**:  
- **Unicast** 🎯 – one-to-one.  
- **Broadcast** 📢 – one-to-all in a subnet (`255.255.255.255` or subnet-specific broadcast).  
- **Multicast** 👥 – one-to-many, group-based communication (Class D).  

---

### 🔹 IPv4 Datagram & Encapsulation
- **Datagram** (IP packet) = basic unit of transfer at Network Layer.  
- Encapsulation process:
  - Transport Layer segment (TCP/UDP) ➡️ wrapped in IP header ➡️ becomes IP packet.  
- **Header fields** include:  
  - **Source IP / Destination IP**  
  - **TTL (Time To Live)** ⏳ – prevents looping, decrements at each hop.  
  - **Protocol field** – indicates if payload is TCP, UDP, ICMP, etc.  

---

### 🔹 IPv4 Address Classes
- **Class A** – 0.0.0.0 – 127.255.255.255 (large networks).  
- **Class B** – 128.0.0.0 – 191.255.255.255 (medium).  
- **Class C** – 192.0.0.0 – 223.255.255.255 (small).  
- **Class D** – 224.0.0.0 – 239.255.255.255 (multicast).  
- **Class E** – 240.0.0.0 – 255.255.255.255 (experimental).  
- Today, the **class system** is replaced by **CIDR**.

---

### 🔹 ARP (Address Resolution Protocol)
- Bridges **Layer 3 (IP)** and **Layer 2 (MAC)**.  
- When a host wants to send data to another host on the LAN:
  - It knows the IP address but not the MAC.  
  - Sends an ARP request (“Who has 192.168.1.1?”).  
  - Device replies with its MAC address.  
- Cached in the **ARP table**.

---

### 🔹 ICMP (Internet Control Message Protocol)
- Used for diagnostics and error reporting.  
- Examples:  
  - **ping** 🏓 – send ICMP Echo Request / receive Echo Reply.  
  - **traceroute** 🧭 – uses ICMP Time Exceeded to show hop-by-hop path.  
- Not for transporting user data but critical for troubleshooting.

---

### 🔹 Subnetting & Masks
- **Subnetting** divides large networks into smaller, manageable segments.  
- **Subnet Mask** defines which part of the IP = network vs host.  
  - Example: `/24` = `255.255.255.0` → 256 addresses, 254 usable hosts.  
- **CIDR (Classless Inter-Domain Routing)** replaces rigid class A/B/C system.  
  - Example: `192.168.1.0/26` → 64 addresses, 62 usable hosts.  

---

### 🔹 Routing Basics
- **Routing** = deciding how to reach a network.  
- **Forwarding** = actual movement of packets from one interface to another.  

#### Routing Table
- A **routing table** is a database that routers (and even PCs) use to decide where to send packets.  
- Contains entries:  
  - **Destination network** (e.g., `192.168.2.0/24`).  
  - **Subnet mask / prefix length** (defines range).  
  - **Next hop** (IP of next router) OR “directly connected”.  
  - **Interface** (outgoing interface).  
  - **Metric** (cost, priority).  

**Example (simplified):**

| Destination  | Subnet Mask     | Next Hop     | Interface | Metric |
|--------------|-----------------|--------------|-----------|--------|
| 0.0.0.0      | 0.0.0.0         | 192.168.1.1  | eth0      | 1      |
| 192.168.1.0  | 255.255.255.0   | On-link      | eth0      | 0      |
| 10.0.0.0     | 255.0.0.0       | 10.0.0.1     | eth1      | 10     |

- The **default route (0.0.0.0/0)** points to the default gateway for unknown destinations.

---

### 🔹 Routing Protocols
- Routers can learn routes **statically** (manual) or **dynamically** (routing protocols).  

#### Interior Gateway Protocols (IGPs)
Used **within one Autonomous System (AS)**.  
1. **Distance Vector Protocols** 🧭  
   - Each router shares routing info with neighbors.  
   - Decisions based on “distance” (hop count).  
   - Example: **RIP (Routing Information Protocol)**.  
   - Pros: simple. Cons: slow convergence, less scalable.  

2. **Link State Protocols** 🌐  
   - Routers exchange full network topology.  
   - Each router builds a complete map of the network.  
   - Example: **OSPF (Open Shortest Path First)**, **IS-IS**.  
   - Pros: scalable, fast convergence.  

#### Exterior Gateway Protocols (EGPs)
Used **between Autonomous Systems**.  
- **BGP (Border Gateway Protocol)** 🛤️  
  - Core routing protocol of the Internet.  
  - Each AS advertises the networks it can reach.  
  - Scalable, policy-based routing.  

---

### 🔹 Autonomous Systems and IANA
- **AS (Autonomous System)** = a group of networks under one administrative domain.  
- Each AS has an **AS Number (ASN)**.  
- **IANA (Internet Assigned Numbers Authority)** manages:  
  - IP address allocation.  
  - ASNs.  
  - DNS root zone.  

---

### 🔹 Non-Routable Address Space
- Reserved for **private use** (RFC 1918).  
  - `10.0.0.0/8`  
  - `172.16.0.0/12`  
  - `192.168.0.0/16`  
- Not routable on the Internet – must use **NAT** to connect outside.  

---

## 📖 Key Terms
- **Network Layer** 🛰️ – responsible for logical addressing, routing, and packet delivery.  
- **IPv4 Address** 🔢 – 32-bit address identifying host and network.  
- **Datagram** 📦 – IP packet with header + payload.  
- **Encapsulation** 🔄 – process of wrapping data with headers.  
- **TTL (Time To Live)** ⏳ – limits packet lifespan.  
- **ARP** 🔍 – maps IP → MAC address.  
- **ICMP** 🏓 – used for diagnostics and error messaging.  
- **Subnetting** ➕➖ – dividing networks into smaller ones.  
- **CIDR** 📐 – classless addressing scheme.  
- **Routing Table** 📑 – database of paths used for packet forwarding.  
- **Distance Vector Protocol** 🧭 – routing based on hop count (e.g., RIP).  
- **Link State Protocol** 🌐 – routing based on network topology (e.g., OSPF).  
- **Path Vector Protocol** 🛤️ – BGP; used between ASes.  
- **Autonomous System (AS)** 🔢 – collection of networks under one authority.  
- **IANA** 🌐 – manages global IPs, ASNs, DNS root.  
- **Private IP** 🔒 – reserved IP ranges for LAN.  
- **Default Route** 🚪 – the “catch-all” route when no specific match is found.  

---

## 💡 Insights
- The **routing table** is like a GPS map: without it, a router can’t forward packets.  
- **Distance Vector vs Link State**:  
  - DV = simple, but inefficient in large networks.  
  - LS = more complex, but powerful for enterprise-scale networks.  
- **BGP** is the glue of the Internet – without it, global routing wouldn’t exist.  
- **Private IP + NAT** explain how billions of devices can share a limited IPv4 space.  
- Tools like **ping** and **traceroute** use ICMP and TTL to test paths and connectivity.  

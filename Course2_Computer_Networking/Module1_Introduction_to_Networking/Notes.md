# 🌐 Course 2 – Module 1: Introduction to Networking

## 📝 Notes

### 🔹 What is Networking?
- **Computer Networking** 💻 – the practice of connecting computers and devices so they can share information and resources.  
- Examples:  
  - **LAN (Local Area Network)** 🏠 – local, small scale (home, office).  
  - **WAN (Wide Area Network)** 🌍 – connects multiple LANs across large distances.  
  - **Internetwork** 🌐 – a collection of networks connected by routers, e.g. the Internet.  

---

### 🔹 Physical Layer
- **Cables** 🔌 – the medium for transmitting data between devices.  
- **Copper Cables** 🧵 – use electrical signals; most common is twisted pair.  
  - Categories: Cat5, Cat5e, Cat6 (differ in speed & resistance to interference).  
  - **Crosstalk** 🔊 – unwanted signal interference between wires.  
- **Fiber Optic Cables** 💡 – use pulses of light; faster and immune to electrical interference.  
- **Line Coding & Modulation** 📶 – techniques to represent digital data on physical media.  

---

### 🔹 Data Link Layer
- Introduces the first networking protocols (Ethernet).  
- **Ethernet** 🔗 – most widely used protocol for sending data across links.  
- **Ethernet Frame** 📦 – structured data unit that includes:  
  - **Preamble & Start Frame Delimiter (SFD)** 📏 – synchronization.  
  - **Destination MAC Address** 🎯 – hardware address of the recipient.  
  - **Source MAC Address** 📤 – sender’s hardware address.  
  - **EtherType / VLAN Header** 🏷️ – indicates which protocol is used.  
  - **Payload** 📄 – actual transmitted data.  
  - **Frame Check Sequence (CRC)** ✅ – error detection.  
- **Broadcast** 📢 – message sent to all devices in the LAN.  
- **Multicast** 👥 – sent to a group of devices.  
- **Unicast** 🎯 – sent to one device only.  
- **Collision Domain** ⚠️ – a network segment where only one device can send data at a time.  
- **Hub vs Switch** 🔀  
  - **Hub** – repeats data to all devices.  
  - **Switch** – sends data only to the intended recipient.  

---

### 🔹 Network Layer
- Responsible for communication across different networks.  
- Uses **Internet Protocol (IP)** 🌍 – IPv4 and IPv6.  
- **Router** 🛣️ – forwards data between independent networks.  
- Works with **BGP (Border Gateway Protocol)** 🌐 – allows routers to share routes.  

---

### 🔹 Transport & Application Layers (Preview)
- **TCP (Transmission Control Protocol)** 📦 – reliable, connection-oriented.  
- **UDP (User Datagram Protocol)** ⚡ – fast, connectionless.  
- These will be studied in detail in later modules.  

---

### 🔹 Models of Networking
- **Five Layer Model** (Physical, Data Link, Network, Transport, Application).  
- **OSI Model** (seven layers) – more detailed industry reference.  

---

## 📖 Key Terms

- **Bit** – the smallest unit of data a computer understands (0 or 1).  
- **Ethernet** 🔗 – protocol for sending data across a link.  
- **Ethernet Frame** 📦 – structured packet of Ethernet data.  
- **MAC Address** 🖥️ – unique 48-bit hardware identifier for network interfaces.  
- **Broadcast / Multicast / Unicast** 📢👥🎯 – different transmission types.  
- **Hub** – physical device that broadcasts data to all nodes.  
- **Switch** – device that sends data only to the correct destination.  
- **Router** 🛣️ – device that forwards data between networks.  
- **Collision Domain** ⚠️ – segment where collisions can occur.  
- **CRC (Cyclical Redundancy Check)** ✅ – mathematical error-checking method.  
- **Preamble & SFD** 📏 – synchronization part of an Ethernet frame.  
- **Payload** 📄 – actual data in a frame or packet.  
- **IP (Internet Protocol)** 🌍 – protocol for addressing and routing across networks.  
- **BGP (Border Gateway Protocol)** 🌐 – routing protocol for exchanging routes between networks.  
- **LAN** 🏠 – local area network.  
- **ISP** 🌍 – Internet Service Provider.  
- **Internetwork** 🌐 – collection of interconnected networks.  
- **Full Duplex / Half Duplex / Simplex** 🔄 – communication directions.  
- **Hexadecimal** 🔢 – base-16 numbering system used in MAC/IP addressing.  

---

## 💡 Insights
- Networking starts with the **physical medium** (cables, signals) and builds upward through layers.  
- **Ethernet** dominates local networking, with frames carrying structured information.  
- **Switches replaced hubs** because they prevent unnecessary traffic and collisions.  
- **Models (5-layer, OSI)** provide a way to understand where technologies and protocols fit.  
- **Error detection (CRC, checksums)** is vital for reliable communication.  

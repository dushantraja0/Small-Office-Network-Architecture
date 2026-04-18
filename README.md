# Small-Office-Network-Architecture
A comprehensive network simulation featuring VLAN segmentation, Router-on-a-Stick (RoAS) configuration, and centralized DHCP/DNS services for a departmental office environment using Cisco Packet Tracer.

# 🌐 Enterprise-Grade Network Design & Implementation

## 📖 Project Abstract
This project showcases the design and deployment of a scalable **Local Area Network (LAN)** for a corporate office environment. The primary goal was to engineer a segmented architecture for four functional domains: **HR, Sales, IT, and a Centralized Server Farm**, ensuring logical isolation and efficient inter-departmental routing.

---

## 🚀 Core Technical Features
- **Hierarchical Network Model:** Structured using a Three-Layer model (Core, Distribution, and Access) for high performance and scalability.
- **Logical Segmentation:** Implemented **VLANs** to minimize broadcast domains and enhance departmental security.
- **Inter-VLAN Routing:** Configured **Router-on-a-Stick (RoAS)** using **802.1Q encapsulation** on a central Cisco 2911 Router.
- **Advanced DHCP Services:** - Implemented a **DHCP Relay Agent (IP Helper-Address)** to facilitate dynamic IP provisioning across different subnets.
  - Automated IP management using departmental address pools.
- **Infrastructure Services:** Configured a **DNS Server** for internal hostname resolution (e.g., `office.com`) and a **Web Server** to host an internal HTML portal.

---

## 🏗 Network Topology
![Network Topology](assets/topology_screenshot.png)
*Architecture featuring a centralized router-based core with departmental node isolation.*

---

## 📊 IP Addressing Strategy (Class C)
| Department | Subnet | Gateway | VLAN ID |
| :--- | :--- | :--- | :--- |
| **HR** | 192.168.10.0/24 | 192.168.10.1 | 10 |
| **Sales** | 192.168.20.0/24 | 192.168.20.1 | 20 |
| **IT** | 192.168.30.0/24 | 192.168.30.1 | 30 |
| **Servers** | 192.168.100.0/24 | 192.168.100.1 | 100 |


---

## 🛠 Configuration Snapshots (CLI)
### Inter-VLAN & DHCP Relay
```bash
! Configuring Sub-interface for HR VLAN
interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0
 ip helper-address 192.168.100.2

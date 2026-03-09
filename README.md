# 🏥 Hospital Network Design and Implementation

## 📌 Project Overview
This project presents the design and implementation of a scalable hospital network infrastructure using enterprise networking principles. The network architecture simulates a real-world healthcare environment with secure communication between headquarters and branch hospital locations.

The design focuses on high availability, network segmentation, routing efficiency, and secure communication while supporting multiple hospital departments and centralized services.

---

# 🏗 Network Architecture

The network follows a hierarchical three-tier architecture to ensure scalability and reliability.

### Core Infrastructure
Each hospital site includes:

- 1 Core Router
- 2 Multilayer Switches (Distribution Layer)
- Multiple Access Switches (Access Layer)

### Key Features
- Redundant multilayer switching for fault tolerance
- Load-balanced traffic handling
- Secure communication between HQ and Branch sites
- Wireless connectivity for users across departments

### Site Connectivity
The Headquarters (HQ) and Branch Hospital networks are connected using serial point-to-point links for site-to-site communication.

---

# 🧩 VLAN Segmentation

The hospital network is segmented into 13 VLANs to improve security, performance, and traffic isolation.

## HQ Network VLANs

| Department | VLAN ID |
|------------|---------|
| MLOCS | 10 |
| MER | 20 |
| MRM | 30 |
| IT | 40 |
| CS | 50 |
| HQ-GWA | 60 |

## Server-Side Site

| Services | VLAN ID |
|----------|---------|
| DHCP, DNS, Email, Web Servers | 70 |

## Branch Network VLANs

| Department | VLAN ID |
|------------|---------|
| NSO | 80 |
| HL | 90 |
| HR | 100 |
| MK | 110 |
| FIN | 120 |
| BR-GWA | 130 |

VLAN segmentation improves network security, reduces broadcast traffic, and allows efficient traffic management between departments.

---

# 🌐 IP Addressing Scheme

The network uses private IP addressing with subnetting for efficient network management.

### HQ Network Base Address
192.168.100.0/24

| Department | Network Address | Subnet Mask |
|------------|----------------|-------------|
| MLOCS | 192.168.100.0 | /26 |
| MER | 192.168.100.64 | /26 |
| MRM | 192.168.100.128 | /26 |
| IT | 192.168.100.192 | /26 |
| CS | 192.168.101.0 | /26 |
| HQ-GWA | 192.168.101.64 | /26 |

### Branch Network Addressing

| Department | Network Address | Subnet Mask |
|------------|----------------|-------------|
| NSO | 192.168.101.128 | /27 |
| HL | 192.168.101.160 | /27 |
| HR | 192.168.101.192 | /27 |
| MK | 192.168.101.224 | /27 |
| FIN | 192.168.102.0 | /27 |
| BR-GWA | 192.168.102.32 | /27 |

---

# 🖧 Server Side Site (SSS)

The server-side network hosts centralized services including:

- DHCP Server
- DNS Server
- Email Server
- Web Server

Network Address:
192.168.102.64/28

This allows centralized management of network services across both HQ and Branch locations.

---

# 🔗 Network Infrastructure Links

Router and multilayer switch connections use /30 networks for point-to-point communication.

| Connection | Network |
|-----------|---------|
| HQR1 → HQMLSW1 | 192.168.102.80/30 |
| HQR1 → HQMLSW2 | 192.168.102.84/30 |
| BRR1 → BRMLSW1 | 192.168.102.88/30 |
| BRR1 → BRMLSW2 | 192.168.102.92/30 |
| HQR1 → BRR1 | 192.168.102.96/30 |

---

# 🌍 Internet Connectivity

Public IP ranges used between routers and ISPs:

195.136.17.0/30  
195.136.17.4/30  
195.136.17.8/30  
195.136.17.12/30  

These networks provide internet connectivity to the hospital network.

---

# ⚙️ Routing Protocol

The network uses the OSPF (Open Shortest Path First) routing protocol.

### Configuration
- OSPF Process ID: 10
- Single area design
- Implemented on routers and multilayer switches

### Advantages
- Fast network convergence
- Efficient path selection
- Scalable routing architecture
- Supports hierarchical network design

---

# 🌐 NAT and PAT

Network Address Translation (NAT) allows internal devices to access external networks.

Implemented on:
- HQ Router
- Branch Router

Features:
- PAT (Port Address Translation) allows multiple internal hosts to share a single public IP address.

---

# 🔒 Access Control Lists (ACL)

ACLs are used to filter network traffic and control communication between networks.

Example:
Access-list 1 permit 192.168.100.0 0.0.0.63  
Access-list 1 permit 192.168.101.0 0.0.0.63  

ACLs help enhance network security by controlling permitted traffic.

---

# 🔐 Site-to-Site VPN

An IPSec VPN tunnel connects the HQ and Branch routers securely.

Benefits:
- Encrypted communication
- Secure inter-site connectivity
- Protection against network interception

---

# 🔄 Inter-VLAN Routing

Inter-VLAN routing is implemented using Layer 3 switches.

Benefits:
- Efficient communication between departments
- Reduced router load
- Faster internal traffic routing

---

# 📡 Wireless Network

Wireless access points are deployed across departments to provide wireless connectivity.

Features:
- Department-based SSIDs
- Secure wireless access for hospital staff
- Mobility within the network

---

# 🛡 Additional Security Features

- SSH remote device management
- Port security configured on server-side switches
- VLAN-based network segmentation
- Secure routing infrastructure

---

# 🧰 Technologies Used

- Cisco Packet Tracer
- VLAN Configuration
- Inter-VLAN Routing
- OSPF Routing Protocol
- NAT / PAT
- Access Control Lists
- IPSec VPN
- DHCP Server
- DNS Server
- Wireless Networking

---

# 🎯 Learning Outcomes

This project helped develop practical skills in:

- Enterprise network architecture design
- Network segmentation and VLAN implementation
- Dynamic routing using OSPF
- NAT and ACL configuration
- VPN deployment
- Real-world network simulation using Cisco technologies




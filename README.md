# Cisco Packet Tracer – DHCP & Router Security Lab

![Cisco Packet Tracer](https://img.shields.io/badge/Cisco-Packet%20Tracer-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white)
![Networking](https://img.shields.io/badge/Networking-CCNA-blue?style=for-the-badge)
![Cisco IOS](https://img.shields.io/badge/Cisco-IOS-0B1F33?style=for-the-badge)
![DHCP](https://img.shields.io/badge/Protocol-DHCP-green?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

## Overview 
   
This Cisco Packet Tracer lab demonstrates the configuration of a basic
LAN using a **Cisco 2811 Router**, **Cisco 2960 Switch**, and **five
client PCs**.

The lab focuses on **DHCP-based IP address assignment**, IPv4
networking, Cisco IOS command-line configuration, and basic router
access security.

The objective was to configure, test, and verify a functional network
using the **Cisco IOS Command-Line Interface (CLI)**.

---

## Objectives

The main objectives of this lab were to:

- Configure a Cisco router interface with an IPv4 address
- Configure the router as a DHCP server
- Create a DHCP address pool
- Configure automatic IP address assignment
- Exclude specific IP addresses from the DHCP pool
- Configure the default gateway and DNS server
- Configure enable password and enable secret
- Secure console access
- Secure VTY access
- Enable password encryption
- Verify DHCP address assignment
- Practice Cisco IOS CLI commands

---

## Network Topology

The lab topology consists of:

- **1 × Cisco 2811 Router**
- **1 × Cisco 2960 Switch**
- **5 × PCs**
- Ethernet connections between the network devices

### Logical Topology

<img width="412" height="379" alt="Screenshot 2026-09-15 124902" src="https://github.com/user-attachments/assets/5b01894b-73f8-463c-8ba2-46fe3e84ea7f" />


## IP Addressing Scheme

The lab uses the private IPv4 network:

**`192.168.1.0/24`**

| Device / Service         | Configuration               |
| ------------------------ | --------------------------- |
| Network Address          | `192.168.1.0/24`            |
| Subnet Mask              | `255.255.255.0`             |
| Router / Default Gateway | `192.168.1.100`             |
| DNS Server               | `192.168.1.100`             |
| DHCP Start Address       | `192.168.1.6`               |
| DHCP End Address         | `192.168.1.254`             |
| Excluded Addresses       | `192.168.1.1 – 192.168.1.5` |

---

## DHCP Client Address Assignment

The PCs were configured to obtain their IPv4 configuration
automatically using DHCP.

| PC  | IPv4 Address   | Subnet Mask     | Default Gateway | Assignment |
| --- | -------------- | --------------- | --------------- | ---------- |
| PC1 | `192.168.1.6`  | `255.255.255.0` | `192.168.1.100` | DHCP       |
| PC2 | `192.168.1.7`  | `255.255.255.0` | `192.168.1.100` | DHCP       |
| PC3 | `192.168.1.8`  | `255.255.255.0` | `192.168.1.100` | DHCP       |
| PC4 | `192.168.1.9`  | `255.255.255.0` | `192.168.1.100` | DHCP       |
| PC5 | `192.168.1.10` | `255.255.255.0` | `192.168.1.100` | DHCP       |

The clients successfully received their:

* IPv4 address
* Subnet mask
* Default gateway
* DNS server

from the router's DHCP service.

---

# DHCP Server Configuration

The Cisco 2811 router was configured to provide DHCP services to
the connected clients.

## 1. Create the DHCP Pool

```text
Router(config)#ip dhcp pool ccna
```

## 2. Configure the Network

```text
Router(dhcp-config)#network 192.168.1.0 255.255.255.0
```

## 3. Configure the Default Gateway

```text
Router(dhcp-config)#default-router 192.168.1.100
```

## 4. Configure the DNS Server

```text
Router(dhcp-config)#dns-server 192.168.1.100
```

## 5. Exclude IP Addresses

```text
Router(config)#ip dhcp excluded-address 192.168.1.1 192.168.1.5
```

The excluded addresses are prevented from being dynamically assigned
by DHCP.

This allows specific addresses to remain available for infrastructure
or manually configured devices.

---

# Router Security Configuration

Basic Cisco IOS security configurations were applied to protect
privileged, console, and VTY access.

## 1. Enable Password

```text
Router(config)#enable password ccna
```

## 2. Enable Secret

```text
Router(config)#enable secret ccnp
```

The `enable secret` command provides a more secure alternative to the
plain-text enable password.

## 3. Password Encryption

```text
Router(config)#service password-encryption
```

This command encrypts passwords stored in the running configuration
that are otherwise displayed in plain text.

## 4. Console Line Security

```text
Router(config)#line console 0
Router(config-line)#password ccna
Router(config-line)#login
```

This configuration requires a password when accessing the router
through the console line.

## 5. VTY Line Security

```text
Router(config)#line vty 0 4
Router(config-line)#password ccna
Router(config-line)#login
```

This configuration provides password-based protection for VTY lines
used for remote terminal access.

---

# Cisco IOS CLI

This lab provided hands-on practice with the Cisco IOS
Command-Line Interface.

Important commands practiced include:

```text
enable
configure terminal
interface fastethernet 0/0
ip address
no shutdown
ip dhcp pool
network
default-router
dns-server
ip dhcp excluded-address
enable password
enable secret
service password-encryption
line console 0
line vty 0 4
password
login
show running-config
copy running-config startup-config
```

---

# Verification & Testing

The network configuration was verified through Packet Tracer by
checking the IP configuration of the client PCs.

The PCs successfully obtained IPv4 addresses from the configured
DHCP pool.

### DHCP Verification

Example client configuration:

```text
IPv4 Address:    192.168.1.6
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.1.100
DNS Server:      192.168.1.100
```

The subsequent clients received addresses from the same DHCP pool.

---

# Lab Evidence

Screenshots included with this project demonstrate:

1. Complete Packet Tracer network topology
2. Router interface configuration
3. DHCP-enabled client PCs
4. Automatic IPv4 address assignment
5. DHCP pool configuration
6. DHCP IP address exclusion
7. Router password configuration
8. Console and VTY line security
9. Password encryption configuration

---

# Technologies & Concepts Practiced

### Networking

* Cisco 2811 Router
* Cisco 2960 Switch
* IPv4 Addressing
* Subnet Mask
* Default Gateway
* LAN Configuration
* Ethernet Networking

### DHCP

* DHCP Server Configuration
* DHCP Pool
* Automatic IP Address Assignment
* DHCP Excluded Addresses
* Default Gateway Assignment
* DNS Server Assignment

### Cisco IOS & Security

* Cisco IOS CLI
* Privileged EXEC Mode
* Global Configuration Mode
* Enable Password
* Enable Secret
* Console Password
* VTY Password
* Password Encryption
* Basic Router Access Security

---

# Learning Outcomes

Through this hands-on lab, I strengthened my practical understanding
of:

* IPv4 network addressing
* Cisco router configuration
* DHCP operation
* Automatic IP address assignment
* DHCP address exclusion
* Cisco IOS commands
* Basic router security
* Console and VTY access
* Network configuration verification
* Troubleshooting fundamentals

This lab demonstrates the importance of configuring, testing,
troubleshooting, and verifying each part of a network.

---

# Key Takeaway

> **Configure. Test. Troubleshoot. Verify.**

Hands-on Packet Tracer practice helps bridge the gap between
networking theory and practical Cisco network configuration.

---

# Tools Used

* **Cisco Packet Tracer**
* **Cisco IOS CLI**
* **Cisco 2811 Router**
* **Cisco 2960 Switch**

---

# Author

**Farhan Ali**

**CCNA | Networking & Network Automation**

Career Path:

**CCNA → CCNP → Cloud Network Engineer**

---


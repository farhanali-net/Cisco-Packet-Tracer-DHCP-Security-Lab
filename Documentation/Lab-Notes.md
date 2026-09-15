# Lab Notes — DHCP & Router Security

## 1. Lab Purpose

The purpose of this lab was to practice basic Cisco router configuration, DHCP services, IPv4 addressing, and router access security using Cisco Packet Tracer.

The lab provided hands-on experience with configuring a Cisco router and verifying network connectivity and automatic IP address assignment.

---

## 2. Devices Used

- Cisco 2811 Router
- Cisco 2960 Switch
- 5 × PCs
- Ethernet connections

---

## 3. Network Topology

The lab consists of a Cisco 2811 router connected to a Cisco 2960 switch. Five PCs are connected to the switch.

```text
                 Cisco 2811 Router
                 192.168.1.100
                        |
                        |
                 Cisco 2960 Switch
                  /   /   \   \   \
                 /   /     \   \   \
               PC1 PC2     PC3 PC4 PC5
````

---

## 4. IP Addressing

The network uses the private IPv4 network:

```text
Network Address:    192.168.1.0/24
Subnet Mask:        255.255.255.0
Default Gateway:    192.168.1.100
DNS Server:         192.168.1.100
```

The router interface was configured with:

```text
192.168.1.100/24
```

---

## 5. DHCP Configuration

The Cisco 2811 router was configured as the DHCP server for the LAN.

### DHCP Pool

```text
ip dhcp pool ccna
network 192.168.1.0 255.255.255.0
default-router 192.168.1.100
dns-server 192.168.1.100
```

### DHCP IP Address Exclusion

The following IP addresses were excluded from dynamic assignment:

```text
ip dhcp excluded-address 192.168.1.1 192.168.1.5
```

Therefore, the available DHCP addresses begin from:

```text
192.168.1.6
```

This allows the excluded addresses to remain available for devices or services that may require manually configured IP addresses.

---

## 6. Automatic IP Address Assignment

The client PCs were configured to obtain their IPv4 settings automatically through DHCP.

The clients successfully received addresses from the DHCP pool.

| PC  | IPv4 Address | Subnet Mask   | Default Gateway | Assignment |
| --- | ------------ | ------------- | --------------- | ---------- |
| PC1 | 192.168.1.6  | 255.255.255.0 | 192.168.1.100   | DHCP       |
| PC2 | 192.168.1.7  | 255.255.255.0 | 192.168.1.100   | DHCP       |
| PC3 | 192.168.1.8  | 255.255.255.0 | 192.168.1.100   | DHCP       |
| PC4 | 192.168.1.9  | 255.255.255.0 | 192.168.1.100   | DHCP       |
| PC5 | 192.168.1.10 | 255.255.255.0 | 192.168.1.100   | DHCP       |

This verified that the router's DHCP service was functioning correctly.

---

## 7. Router Security Configuration

Basic router access security was configured using Cisco IOS commands.

### Enable Password

```text
enable password ccna
```

An enable password was configured to protect privileged EXEC mode.

### Enable Secret

```text
enable secret ccnp
```

An enable secret was also configured for privileged EXEC access.

### Password Encryption

```text
service password-encryption
```

Password encryption was enabled so that applicable passwords stored in the router configuration are not displayed as plain text.

---

## 8. Console Line Security

Console access was protected with a password.

```text
line console 0
password ccna
login
```

The `login` command requires the configured console password when accessing the router through the console line.

---

## 9. VTY Line Security

VTY lines were configured for password-based access.

```text
line vty 0 4
password ccna
login
```

This provides basic authentication for VTY terminal access.

---

## 10. Cisco IOS CLI Commands Practiced

The following Cisco IOS commands were practiced during the lab:

```text
enable
configure terminal
interface fastethernet 0/0
ip address
no shutdown
ip dhcp excluded-address
ip dhcp pool
network
default-router
dns-server
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

## 11. DHCP Verification

The DHCP configuration was verified by checking the IPv4 configuration of the client PCs.

Each client was checked for:

* IPv4 address
* Subnet mask
* Default gateway
* DNS server
* DHCP assignment

The clients successfully received valid IPv4 addresses from the configured DHCP pool.

---

## 12. Network Verification

The network configuration was tested using Cisco Packet Tracer.

Verification included:

* Checking router interface configuration
* Checking PC IP configuration
* Confirming DHCP address assignment
* Confirming the correct default gateway
* Checking router security configuration
* Testing network connectivity

---

## 13. Troubleshooting Approach

The lab followed a basic networking troubleshooting workflow:

```text
Configure
    ↓
Check
    ↓
Test
    ↓
Identify the Problem
    ↓
Correct the Configuration
    ↓
Verify Again
```

This workflow helps develop practical troubleshooting skills that are important in real-world network support and network engineering environments.

---

## 14. Key Technologies & Concepts

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
* DHCP IP Address Exclusion
* Default Gateway Assignment
* DNS Server Assignment

### Cisco IOS & Security

* Cisco IOS CLI
* Privileged EXEC Mode
* Global Configuration Mode
* Enable Password
* Enable Secret
* Console Line Security
* VTY Line Security
* Password Encryption
* Basic Router Access Security

---

## 15. Lab Screenshots

The repository contains screenshots showing the practical implementation and verification of the lab.

The screenshots include:

1. Network topology
2. Router configuration
3. DHCP configuration
4. Automatic IP address assignment
5. DHCP IP address exclusion
6. Router security configuration
7. Cisco IOS CLI commands

These screenshots serve as visual evidence of the configurations performed in Cisco Packet Tracer.

---

## 16. Learning Outcomes

This hands-on Packet Tracer lab strengthened my practical understanding of:

* Cisco router configuration
* Cisco IOS command-line interface
* IPv4 addressing
* DHCP
* Automatic IP address assignment
* DHCP IP address exclusion
* Default gateway configuration
* DNS configuration
* Console and VTY authentication
* Password encryption
* Basic network verification
* Troubleshooting fundamentals

The lab helped bridge the gap between networking theory and practical Cisco network configuration.

---

## 17. Conclusion

This Cisco Packet Tracer exercise provided practical experience in configuring a small LAN using Cisco networking devices.

The lab demonstrated how a Cisco router can provide DHCP services while also being configured with basic access-security mechanisms.

Through configuration, testing, and verification, I strengthened my foundational networking skills as part of my ongoing CCNA preparation.

> **Configure. Test. Troubleshoot. Verify.**

---

## 18. Tools Used

* Cisco Packet Tracer
* Cisco IOS CLI
* Cisco 2811 Router
* Cisco 2960 Switch

---

## 19. Project Type

**Hands-on Networking Lab**

**Focus:** Cisco Networking | DHCP | IPv4 | Cisco IOS | Router Security

---

## 20. Career Path

**CCNA → CCNP → Cloud Network Engineer**

This project is part of my continuous networking practice and technical portfolio.

```
```

# Simple-Office-LAN
# Simple Office LAN Design with Static IPs and Telnet (Cisco Packet Tracer)

## Project Overview

This repository showcases a practical network design implemented using Cisco Packet Tracer (version 8.2.2 or higher recommended). The project focuses on creating a functional Local Area Network (LAN) for a small office environment, demonstrating core networking skills essential for a Network Technician.

Key features and skills demonstrated in this project include:

* **Network Topology Design:** Building a hierarchical LAN structure with a router and multiple switches.
* **Static IP Addressing:** Meticulously assigning static IP addresses to all end devices (PCs) and router interfaces within defined subnets.
* **Basic Router Configuration:** Configuring router interfaces to enable communication between different network segments.
* **Telnet Remote Access:** Implementing and verifying Telnet for secure (for lab purposes) remote command-line access to the router, showcasing remote management capabilities.
* **Connectivity Verification:** Utilizing `ping` commands to thoroughly test and confirm end-to-end network connectivity between devices across different segments.
* **Troubleshooting Fundamentals:** The process of designing and implementing this network inherently involves basic troubleshooting to ensure all components function as intended.

This project is a testament to hands-on experience in fundamental network setup, crucial for any aspiring or current network professional.

## Network Topology

The simulated network comprises:

* **One Cisco 1941 Router:** Serves as the central inter-network device, routing traffic between the two LAN segments.
* **Two Cisco 2960 Switches:** Function as access layer switches, connecting end devices within their respective departments/subnets.
* **Four End Devices (PCs):** Representing user workstations, distributed across the two network segments.

The design facilitates internal communication and is structured to allow for future expansion, such as the addition of more devices, servers, or advanced routing protocols.

## IP Addressing Scheme

The following static IP addressing scheme has been implemented:

| Device/Interface    | IP Address    | Subnet Mask     | Default Gateway | Connected To               | Notes                                      |
| :------------------ | :------------ | :-------------- | :-------------- | :------------------------- | :----------------------------------------- |
| **Router (Gig0/0)** | 192.168.1.1   | 255.255.255.0   | N/A             | Switch connected to PC0/PC1 | Main router interface for Subnet 1       |
| **Router (Gig0/1)** | 192.168.2.1   | 255.255.255.0   | N/A             | Switch connected to PC2/PC3 | Main router interface for Subnet 2       |
| **PC0** | 192.168.1.10  | 255.255.255.0   | 192.168.1.1     | Switch 1                   |                                            |
| **PC1** | 192.168.1.11  | 255.255.255.0   | 192.168.1.1     | Switch 1                   |                                            |
| **PC2** | 192.168.2.10  | 255.255.255.0   | 192.168.2.1     | Switch 2                   |                                            |
| **PC3** | 192.168.2.11  | 255.255.255.0   | 192.168.2.1     | Switch 2                   |                                            |

## Configuration Highlights

### Router (Partial Configuration Snippet)

```cli
enable
configure terminal
hostname Router
!
interface GigabitEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown
!
interface GigabitEthernet0/1
 ip address 192.168.2.1 255.255.255.0
 no shutdown
!
line vty 0 4
 password cisco
 login
 transport input all
!
end
write memory

Enterprise Network Foundation
Overview

This project establishes the foundation of a virtual enterprise network that will be expanded throughout future labs. The objective is to design, configure, and document a small business network using enterprise technologies and networking best practices.

The environment consists of a pfSense firewall/router, a Windows Server, and a Windows client connected through separate WAN and LAN networks. This lab focuses on establishing reliable network connectivity, implementing an IP addressing scheme, and validating communication between systems.

Objectives
Design a basic enterprise network topology
Configure pfSense as the network gateway and firewall
Create separate WAN and LAN networks
Configure static and dynamic IPv4 addressing
Verify network connectivity between all systems
Document the environment using professional engineering practices
Lab Environment
Component	Purpose
Oracle VirtualBox	Virtualization Platform
pfSense	Firewall / Router
Windows Server	Infrastructure Server
Windows 10/11	Client Workstation
Network Topology
                 Internet
                     │
              NAT Network (WAN)
                     │
                +------------+
                |  pfSense   |
                | Firewall   |
                +------------+
                     │
         Internal Network (192.168.10.0/24)
               │                     │
     Windows Server          Windows Client
      192.168.10.10             DHCP
IP Addressing
Device	IP Address	Role
pfSense LAN	192.168.10.1	Default Gateway
Windows Server	192.168.10.10	Infrastructure Server
Windows Client	DHCP	Client Workstation
Technologies Used
Oracle VirtualBox
pfSense
Windows Server
Windows 10/11
TCP/IP
IPv4
DHCP
NAT
ICMP
Skills Demonstrated
Enterprise network design
Virtual network configuration
Static IP configuration
DHCP configuration
Network segmentation
Basic routing concepts
Connectivity validation
Infrastructure documentation
Technical troubleshooting
Validation

Connectivity was verified by testing communication between all devices.

Validation included:

Successful communication between the Windows Server and pfSense
Successful communication between the Windows Client and pfSense
Successful communication between the Windows Client and Windows Server
Internet connectivity verification
DNS name resolution testing
Documentation

Project documentation includes:

Network topology diagram
IP addressing plan
Configuration screenshots
Connectivity test results
Troubleshooting notes
Lessons learned
Lessons Learned

This lab reinforced the importance of proper network planning before deploying infrastructure. Separating WAN and LAN networks, assigning appropriate IP addresses, and validating connectivity created a solid foundation for future services such as Active Directory, DNS, DHCP, Group Policy, VLANs, VPNs, and network monitoring.

Future Enhancements

This environment will be expanded in future labs to include:

Active Directory Domain Services
DNS
DHCP
Group Policy
File Services
VLANs
VPN Configuration
Windows Deployment Services
Network Monitoring
Enterprise Security Controls

# Enterprise Network Foundation

## Overview

This project establishes the foundation of a virtual enterprise network using Oracle VirtualBox, pfSense, Windows Server 2022, and Windows 10. The objective was to design, configure, and validate a small business network that will serve as the base infrastructure for future enterprise services including Active Directory, DNS, DHCP, Group Policy, VLANs, VPNs, and network monitoring.

---

## Lab Environment

| Component | Purpose |
|-----------|----------|
| Oracle VirtualBox | Virtualization Platform |
| pfSense | Firewall / Router |
| Windows Server 2022 | Infrastructure Server |
| Windows 10 | Client Workstation |

---

## Network Architecture

```
                Internet
                    │
            VirtualBox NAT
                    │
            ┌────────────────┐
            │    pfSense     │
            │ Firewall/Router│
            └────────────────┘
             WAN         LAN
              │           │
      10.0.2.x      192.168.1.1/24
                          │
          ┌───────────────┴───────────────┐
          │                               │
 Windows Server 2022             Windows 11 Client
  Static IP                      DHCP Client
```

---

## Technologies Used

- Oracle VirtualBox
- pfSense
- Windows Server 2022
- Windows 10
- IPv4
- TCP/IP
- DHCP
- NAT
- ICMP

---

## pfSense Configuration

The first step was configuring pfSense to act as the network gateway. The WAN interface was connected to the VirtualBox NAT network to provide internet access, while the LAN interface was configured with a static IP address of **192.168.1.1/24**. A DHCP scope of **192.168.1.100–192.168.1.200** was created to automatically assign addresses to client devices.


<img width="624" height="415" alt="pfsense_Linux_config" src="https://github.com/user-attachments/assets/f01bc278-ba09-457f-8495-405984f2398b" />

Figure 1. pfSense configured with a WAN interface connected to the VirtualBox NAT network and a LAN interface configured with a static IP address of 192.168.1.1/24.

---
## Windows Server Configuration

Windows Server 2022 was configured with a static IPv4 address outside of the DHCP scope to ensure a consistent address for future infrastructure services such as Active Directory and DNS.

The server successfully established connectivity to the pfSense management interface.

<img width="624" height="500" alt="Windows_server_ipconfig" src="https://github.com/user-attachments/assets/0aba4dae-a457-459e-8b4f-e4b66b2e1aa8" />

Figure 2. Windows Server 2022 configured with a static IPv4 address (192.168.1.10/24) using pfSense (192.168.1.1) as the default gateway.

---
## Windows 10 Client Configuration

The Windows 10 workstation was configured to obtain an IP address automatically through DHCP. After connecting to the internal network, the workstation successfully received an address from the pfSense DHCP server.

<img width="624" height="443" alt="Windows_user_ipconfig" src="https://github.com/user-attachments/assets/b76a7b7b-4d06-4293-a307-2ec2ae86c818" />

Figure 3. Windows 10 workstation successfully receiving a DHCP lease (192.168.1.100) from the pfSense DHCP server.

---
## Validation

The following tasks were successfully completed:

- Configured pfSense as the network gateway
- Configured separate WAN and LAN interfaces
- Assigned a static LAN IP address
- Enabled DHCP services
- Assigned a static IP address to Windows Server
- Successfully obtained a DHCP lease on Windows 11
- Verified management access to the pfSense web interface


---

## Lessons Learned

This lab reinforced the importance of establishing a properly designed network before deploying enterprise services. Separating WAN and LAN traffic through pfSense, assigning static addresses to infrastructure devices, and using DHCP for client systems created a stable and scalable foundation for future expansion.


---

## Next Steps

The environment created in this lab will be expanded to include:

- Active Directory Domain Services
- DNS
- DHCP Management
- Group Policy
- File Services
- VLAN Segmentation
- VPN Connectivity
- Windows Deployment Services
- Network Monitoring
- Enterprise Security Controls

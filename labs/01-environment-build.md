# Windows Server and Active Directory Environment Build

## Overview

Built a small Windows domain environment in VMware Workstation to practice Active Directory administration, Windows support, networking, and troubleshooting.

The environment includes a domain controller, Windows 10 workstation, and Windows Server 2022 member server.

## Lab Environment

| System | Operating System | Role |
|---|---|---|
| Domain Controller | Windows Server 2019 | AD DS, DNS, DHCP, and routing |
| CLIENT1 | Windows 10 | Domain-joined workstation |
| MBR-SRV01 | Windows Server 2022 | Domain-joined member server |

## Network Configuration

- Internal network: VMware LAN Segment
- Subnet: `172.16.0.0/24`
- Domain controller: `172.16.0.1`
- DNS and DHCP provided by the domain controller
- Domain members receive network settings through DHCP
- Domain: `domian.local`

## Work Completed

- Created and configured Windows virtual machines
- Installed Windows Server 2019 and Windows Server 2022
- Installed Active Directory Domain Services
- Created a new Active Directory forest and domain

### DNS Configuration

![DNS configuration](/Screenshots/dns-config.jpg)

### DHCP Configuration

![DHCP configuration](/Screenshots/dhcp-config.jpg)

### Active Directory Domain and Computer Accounts

![Active Directory domain and computer accounts](/Screenshots/ad-comp-con.jpg)
### CLIENT1 Domain Membership

![CLIENT1 domain membership](/Screenshots/Client01.jpg)

### MBR-SRV01 Domain Membership

![MBR-SRV01 domain membership](/Screenshots/Mbr-srv.jpg)

## Verification

The environment was verified using:

- `ipconfig /all`
- `nslookup domian.local`
- Domain sign-in testing
- Active Directory Users and Computers
- Windows System Properties

## Skills Demonstrated

- Windows Server administration
- Active Directory Domain Services
- DNS and DHCP
- Windows domain joins
- Computer account management
- VMware networking
- IPv4 configuration
- Basic Windows and network troubleshooting


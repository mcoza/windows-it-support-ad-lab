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
- Configured DNS and DHCP
- Configured routing between the internal network and VMware NAT
- Joined CLIENT1 to the domain
- Joined MBR-SRV01 to the domain
- Verified both computer accounts in Active Directory Users and Computers
- Signed in to CLIENT1 using a domain user account

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

## Screenshots

### Active Directory Computer Accounts

CLIENT1 and MBR-SRV01 appear as domain computer accounts in Active Directory Users and Computers.

![Active Directory computer accounts](../../../Screenshots/ad-comp.png)

### CLIENT1 Domain Membership

CLIENT1 is joined to the `domian.local` Active Directory domain.

![CLIENT1 domain membership](../../Screenshots/Client01.png)

### Member Server Domain Membership

MBR-SRV01 is joined to the `domian.local` Active Directory domain.

![Member server domain membership](../../Screenshots/Mbr-srv.png)

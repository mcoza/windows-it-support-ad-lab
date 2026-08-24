# Windows Server and Active Directory Environment Build

## Overview

Built a small Windows domain environment in VMware Workstation to practice Active Directory administration, Windows support, networking, routing, and troubleshooting.

The environment includes a Windows Server 2019 domain controller with two network interfaces, a Windows 10 workstation, and a Windows Server 2022 member server.

## Lab environment

| System | Operating System | Role |
|---|---|---|
| Domain Controller | Windows Server 2019 | AD DS, DNS, DHCP, authentication, RRAS/NAT routing |
| CLIENT1 | Windows 10 | Domain-joined workstation |
| MBR-SRV01 | Windows Server 2022 | Domain-joined member server |

## Network design

The domain controller connects the isolated Active Directory network to VMware's NAT network.

| Component | Configuration |
|---|---|
| External DC interface | Connected to VMware NAT |
| Internal DC interface | `172.16.0.1/24`, no default gateway |
| Internal network | VMware LAN Segment |
| DHCP scope | `172.16.0.100`–`172.16.0.200` |
| Client default gateway | `172.16.0.1` |
| Client DNS server | `172.16.0.1` |
| Domain | `domian.local` |

```text
Internet
   |
VMware NAT
   |
External NIC
   |
Windows Server 2019 DC
AD DS / DNS / DHCP / RRAS NAT
   |
Internal NIC: 172.16.0.1
   |
VMware LAN Segment
   |----------------------|
 CLIENT1              MBR-SRV01
```

## Work completed

- Created and configured the Windows virtual machines in VMware Workstation
- Configured two network interfaces on the domain controller: external VMware NAT and internal LAN Segment
- Assigned `172.16.0.1/24` to the domain controller's internal interface without a default gateway
- Installed Active Directory Domain Services
- Created the `domian.local` Active Directory forest and domain
- Configured DNS on the domain controller
- Configured a DHCP scope for `172.16.0.100`–`172.16.0.200`
- Configured DHCP clients to use `172.16.0.1` as both their default gateway and DNS server
- Configured Routing and Remote Access (RRAS) for NAT between the internal LAN and external VMware NAT interface
- Joined CLIENT1 to the domain
- Joined MBR-SRV01 to the domain
- Verified the resulting computer accounts in Active Directory

## Routing and NAT

Routing was configured through Windows Server **Routing and Remote Access**:

```text
Routing and Remote Access
    -> Configure and Enable Routing and Remote Access
    -> Network Address Translation (NAT)
    -> Select the external "internet" interface as the public interface
```

This allows systems on the isolated `172.16.0.0/24` network to use the domain controller as their router while keeping the internal Active Directory network separate from the VMware NAT network.

## DNS configuration

![DNS configuration](/Screenshots/dns-config.jpg)

## DHCP configuration

![DHCP configuration](/Screenshots/dhcp-config.jpg)

## Active Directory domain and computer accounts

![Active Directory domain and computer accounts](/Screenshots/ad-comp-con.jpg)

## CLIENT1 domain membership

![CLIENT1 domain membership](/Screenshots/Client01.jpg)

## MBR-SRV01 domain membership

![MBR-SRV01 domain membership](/Screenshots/Mbr-srv.jpg)

## Verification

The environment was checked using multiple layers rather than relying on one successful configuration screen:

- `ipconfig /all` to verify client addressing, DNS, and default-gateway configuration
- `nslookup domian.local` to verify domain name resolution
- domain sign-in testing to verify authentication from a joined system
- Active Directory Users and Computers to verify user and computer objects
- Windows System Properties to verify domain membership
- Routing and Remote Access to verify the NAT/routing configuration

## Skills demonstrated

- Windows Server administration
- Active Directory Domain Services
- DNS and DHCP configuration
- Windows Server RRAS and NAT
- Dual-NIC server networking
- Default-gateway and DNS configuration through DHCP
- Windows domain joins
- Computer-account management
- VMware virtual networking
- IPv4 subnetting and addressing
- Windows and network troubleshooting

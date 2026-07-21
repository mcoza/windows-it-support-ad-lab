# windows-it-support-ad-lab
Hands-on Windows Server, Active Directory, networking, Group Policy, access control, and IT support lab built in VMware Workstation.


# Windows Active Directory Environment

## Purpose

Build a small enterprise-style Windows environment for practicing identity management, endpoint support, networking, and security administration.

## Environment

| System    | Operating System    | Purpose |

| DC01      | Windows Server 2019 | Active Directory, DNS, DHCP, routing |

| CLIENT1   | Windows 10          | Domain-joined workstation |

| MBR-SRV01 | Windows Server 2022 | Domain-joined member server |

## Network

- VMware Workstation
- Internal LAN segment
- Internal subnet: 172.16.0.0/24
- Domain controller provides DNS and DHCP
- Domain: domain.local

## Work Completed

- Installed Windows Server
- Installed Active Directory Domain Services
- Created a new forest and domain
- Configured DNS and DHCP
- Joined a Windows workstation to the domain
- Joined a Windows Server member server to the domain
- Verified computer accounts in Active Directory

## Security Relevance

Centralized identity allows administrators to manage users, computers, authentication, permissions, and security settings from one location.

## Verification

- Both computer accounts appear in Active Directory Users and Computers
- Domain users can sign in to CLIENT1
- MBR-SRV01 shows membership in domain.local
- Clients receive valid DHCP and DNS settings

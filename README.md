# Windows IT Support & Active Directory Lab

A hands-on Windows enterprise lab built in VMware Workstation to practice **Windows Server administration, Active Directory, DNS/DHCP, identity management, PowerShell, networking, and troubleshooting**.

This repository documents work completed in the lab with screenshots and short technical write-ups. It represents a personal lab environment, not production or professional work experience.

## Current environment

| System | OS | Role |
|---|---|---|
| Domain Controller | Windows Server 2019 | AD DS, DNS, DHCP, authentication, RRAS/NAT routing |
| CLIENT1 | Windows 10 | Domain-joined workstation |
| MBR-SRV01 | Windows Server 2022 | Domain-joined member server |
| VMware Workstation | Windows host | Virtualization platform |

### Network

- Internal subnet: `172.16.0.0/24`
- Domain controller internal NIC: `172.16.0.1/24`
- Domain controller external NIC: connected to VMware NAT
- Internal NIC has no default gateway
- DHCP scope: `172.16.0.100`–`172.16.0.200`
- Domain members use `172.16.0.1` as their default gateway and DNS server
- Windows Server Routing and Remote Access (RRAS) provides NAT between the isolated internal LAN and the external VMware NAT interface
- Lab domain: `domian.local` *(original lab name retained)*

## Architecture

```text
                         Internet
                            |
                       VMware NAT
                            |
                  External NIC on DC
                            |
                  Windows Server 2019
                    Domain Controller
             AD DS / DNS / DHCP / RRAS NAT
                            |
                  Internal NIC: 172.16.0.1
                            |
                  VMware LAN Segment
                       AD-LAB
                    /             \
                   /               \
         Windows 10              Windows Server 2022
          CLIENT1                   MBR-SRV01
     Domain Workstation          Member Server
```

## Completed labs

| Lab | What it demonstrates |
|---|---|
| [Environment Build](labs/01-environment-build.md) | Windows Server deployment, AD DS, DNS, DHCP, RRAS/NAT routing, domain joins, and connectivity verification |
| [User & OU Management](labs/02-user-and-ou-management.md) | User provisioning, OUs, account attributes, PowerShell automation, LDAP search |
| [Groups & Delegated Administration](labs/03-groups-and-permissions.md) | Security groups, nested groups, PowerShell membership management, delegated permissions |

Supporting evidence is stored in the [`Screenshots`](Screenshots) folder.

## Skills demonstrated

### Windows / IT support

- Windows Server and client configuration
- Domain joins and computer-account verification
- IPv4, DNS, DHCP, routing, and connectivity troubleshooting
- Windows administrative tools
- Technical verification and documentation

### Active Directory / IAM

- Active Directory Domain Services deployment
- User and computer account management
- Organizational Unit design
- Security groups and nested membership
- Account expiration and attribute management
- Password-management delegation
- Least-privilege administration
- PowerShell-based provisioning and group assignment

### Networking

- VMware virtual networking with separate external and internal interfaces
- Internal subnet configuration
- Windows Server RRAS and NAT routing
- DHCP default-gateway and DNS configuration
- DNS and DHCP integration with Active Directory
- `ipconfig` and `nslookup` verification
- Name-resolution and domain-connectivity troubleshooting

## Current status

### Working / completed

- [x] Windows Server 2019 domain controller
- [x] Active Directory forest and domain
- [x] DNS and DHCP configuration
- [x] RRAS/NAT routing between the internal LAN and VMware NAT
- [x] Windows 10 domain-joined client
- [x] Windows Server 2022 domain-joined member server
- [x] Bulk user provisioning with PowerShell
- [x] Organizational Unit and user-attribute management
- [x] Security-group nesting and membership management
- [x] Limited delegated administration

### Planned / in progress

- [ ] Group Policy exercises
- [ ] Account lifecycle / onboarding-offboarding workflow
- [ ] Structured troubleshooting cases
- [ ] Separate standard and privileged identities for delegated administration
- [ ] Additional support documentation as the lab expands

## Repository structure

```text
windows-it-support-ad-lab/
├── README.md
├── labs/
│   ├── 01-environment-build.md
│   ├── 02-user-and-ou-management.md
│   └── 03-groups-and-permissions.md
└── Screenshots/
```

The repository intentionally stays small: only completed work gets its own lab document. Planned work is listed in the roadmap rather than represented by empty placeholder files.

## Security and privacy

This repository contains lab-only information. No production systems, real employee records, passwords, private keys, authentication tokens, or confidential organizational data are included.

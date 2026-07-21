# Windows IT Support and Active Directory Lab

## Overview

This repository documents a hands-on Windows enterprise lab built in VMware Workstation. The environment was created to practice Windows Server administration, Active Directory Domain Services, user and computer management, networking, access control, troubleshooting, and technical documentation.

The project is designed to demonstrate practical skills relevant to IT support, help desk, systems administration, identity and access management, and entry-level cybersecurity roles.

## Lab Environment

| System | Operating System | Role |
|---|---|---|
| Domain Controller | Windows Server 2019 | Active Directory Domain Services, DNS, DHCP, authentication, and internal network services |
| CLIENT1 | Windows 10 | Domain-joined user workstation |
| MBR-SRV01 | Windows Server 2022 | Domain-joined member server |
| VMware Workstation | Windows host | Virtualization platform used to run the lab |

## Network Environment

- Internal network: VMware LAN Segment
- Internal subnet: `172.16.0.0/24`
- Domain controller internal address: `172.16.0.1`
- Domain members receive IP configuration through DHCP
- Domain members use the domain controller for DNS
- The environment uses an isolated virtual network for internal communication

## Technologies Used

- VMware Workstation
- Windows Server 2019
- Windows Server 2022
- Windows 10
- Active Directory Domain Services
- Active Directory Users and Computers
- DNS
- DHCP
- TCP/IP
- IPv4 addressing
- Organizational Units
- Security groups
- Group Policy
- Windows Event Viewer
- PowerShell
- Command Prompt

## Skills Demonstrated

### Windows and IT Support

- Installing and configuring Windows operating systems
- Creating and managing virtual machines
- Configuring network adapters and IPv4 settings
- Troubleshooting startup, installation, DNS, DHCP, and connectivity problems
- Joining workstations and servers to a domain
- Documenting technical configurations and resolutions

### Active Directory Administration

- Deploying an Active Directory forest and domain
- Creating and managing user accounts
- Managing computer accounts
- Creating Organizational Units
- Creating and managing security groups
- Configuring account expiration
- Disabling user accounts
- Resetting user passwords
- Managing user attributes
- Delegating limited administrative permissions
- Applying least-privilege concepts
- Managing domain-joined workstations and member servers

### Networking

- Configuring internal VMware network segments
- Understanding subnets, gateways, DNS, and DHCP
- Verifying network configuration with `ipconfig`
- Testing name resolution with `nslookup`
- Troubleshooting communication between domain systems
- Understanding the relationship between DNS and Active Directory

### Security

- Centralized identity and access management
- Authentication and authorization
- Account lifecycle management
- Group-based access control
- Delegated administration
- Least privilege
- Protected Users
- Network isolation concepts
- Security logging and verification

## Current Lab Architecture

```text
                         Internet
                            |
                       VMware NAT
                            |
                  Windows Server 2019
                    Domain Controller
                   AD DS / DNS / DHCP
                       172.16.0.1
                            |
                  VMware LAN Segment
                       AD-LAB
                    /             \
                   /               \
         Windows 10              Windows Server 2022
          CLIENT1                   MBR-SRV01
     Domain Workstation          Member Server
```


## Lab Projects

1. [Windows Server and Active Directory Environment Build](labs/01-environment-build)
2. [Active Directory User and OU Management](labs/02-user-and-ou-management)
3. [Security Groups and Permissions](labs/03-groups-and-permissions)
4. [Group Policy Administration](labs/04-group-policy)
5. [Account Lifecycle Management](labs/05-account-lifecycle)
6. [Windows and Network Troubleshooting](labs/06-troubleshooting)
7. [IT Support Documentation](documentation)
8. [Lab Diagrams](diagrams)
9. [Lab Screenshots](screenshots)

Additional project pages will be added as the lab progresses.

## What I Have Completed

- Created a Windows Server 2019 domain controller
- Installed Active Directory Domain Services
- Created an Active Directory forest and domain
- Configured DNS and DHCP
- Created domain user accounts
- Joined a Windows 10 workstation to the domain
- Installed Windows Server 2022
- Joined the Windows Server 2022 member server to the domain
- Verified workstation and server computer accounts in Active Directory
- Configured and verified internal network connectivity
- Began Microsoft Active Directory administration exercises

## Project Goals

The goals of this project are to:

- Develop practical Windows support and administration skills
- Understand how Active Directory components work together
- Practice common help-desk and systems-administration tasks
- Connect technical configurations to cybersecurity controls
- Build clear technical documentation
- Demonstrate troubleshooting ability through real lab problems
- Prepare for IT support, IAM, systems administration, and cybersecurity responsibilities

## Security and Privacy Notice

This repository contains only lab information.

No production systems, real employee information, passwords, private keys, authentication tokens, or confidential organizational data are included.

## Project Status

This project is currently in progress. New exercises, screenshots, troubleshooting cases, and documentation will be added as the Active Directory lab develops.

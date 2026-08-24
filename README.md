# Windows IT Support & Active Directory Lab

A small Windows domain lab built in VMware Workstation to practice **Windows Server, Active Directory, DNS/DHCP, networking, PowerShell, and troubleshooting**.

This is personal lab work, not production or professional experience.

## Environment

| System | OS | Role |
|---|---|---|
| Domain Controller | Windows Server 2019 | AD DS, DNS, DHCP, RRAS/NAT |
| CLIENT1 | Windows 10 | Domain-joined workstation |
| MBR-SRV01 | Windows Server 2022 | Domain-joined member server |

### Network

```text
Internet
   |
VMware NAT
   |
Windows Server 2019 DC
AD DS / DNS / DHCP / RRAS NAT
Internal: 172.16.0.1/24
   |
VMware LAN Segment
   |----------------------|
 CLIENT1              MBR-SRV01
```

- internal subnet: `172.16.0.0/24`
- DHCP scope: `172.16.0.100`–`172.16.0.200`
- clients use `172.16.0.1` for DNS and their default gateway
- lab domain: `domian.local` *(original lab name retained)*

## Documented hands-on work

### [Environment Build](labs/01-environment-build.md)
Built the domain environment, configured AD DS/DNS/DHCP and RRAS/NAT, joined a Windows 10 client and Windows Server 2022 member server, and verified connectivity/domain membership.

### [User & OU Management](labs/02-user-and-ou-management.md)
Created and organized Active Directory users and OUs, automated bulk user provisioning with PowerShell, configured account attributes, and verified objects with Active Directory tools and LDAP search.

Supporting screenshots are stored in [`Screenshots/`](Screenshots).

## Skills represented

- Windows Server administration fundamentals
- Active Directory Domain Services
- DNS and DHCP configuration
- Windows Server RRAS/NAT
- Windows domain joins and computer accounts
- Active Directory user and OU management
- PowerShell-based user provisioning
- account attribute management and LDAP filtering
- IPv4 addressing and virtual networking
- connectivity, DNS, and domain troubleshooting

## Next lab areas

Group-based permissions/delegation, Group Policy, and account lifecycle workflows are useful next extensions, but they are not presented here as completed work until they are verified in the lab.

## Note on the domain name

The original build used `domian.local` due to a naming typo. It is kept in the documentation because it reflects the environment that was actually built rather than rewriting the history of the lab.

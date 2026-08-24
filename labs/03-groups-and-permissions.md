# Active Directory Security Groups & Delegated Administration

## Goal

Practice group-based access management and limited administrative delegation in Active Directory.

## Work completed

- Created location-based security groups for Sydney, Melbourne, and Brisbane contractor accounts
- Added each contractor account to its matching group
- Created `GG_Australia_Contractors` and nested the three location groups beneath it
- Created `GG_Bulk_Users` for PowerShell-provisioned accounts
- Used PowerShell to add users from the `_USERS` Organizational Unit to `GG_Bulk_Users`
- Created city administrator groups for Sydney, Melbourne, and Brisbane
- Added the matching contractor account to each city administrator group
- Added the three contractor accounts to the built-in `Protected Users` group
- Delegated password-reset and forced-password-change permissions over the matching city Organizational Units

## Contractor group structure

```text
GG_Australia_Contractors
├── GG_Sydney_Contractors
│   └── SydneyContractor
├── GG_Melbourne_Contractors
│   └── MelbourneContractor
└── GG_Brisbane_Contractors
    └── BrisbaneContractor
```

The nested structure provides one broader contractor group while preserving location-specific membership.

## PowerShell group assignment

PowerShell was used to collect the users located directly inside the `_USERS` OU and add them to `GG_Bulk_Users`.

```powershell
Import-Module ActiveDirectory

$Users = Get-ADUser `
    -SearchBase "OU=_USERS,DC=domian,DC=local" `
    -SearchScope OneLevel `
    -Filter *

Add-ADGroupMember `
    -Identity "GG_Bulk_Users" `
    -Members $Users

$Users.Count
```

## Delegated administration

Limited password-management permissions were delegated at the OU level rather than granting broad domain-administrator privileges.

```text
Sydney OU
└── Sydney Administrators
    └── SydneyContractor

Melbourne OU
└── Melbourne Administrators
    └── MelbourneContractor

Brisbane OU
└── Brisbane Administrators
    └── BrisbaneContractor
```

Delegated permissions covered:

- resetting user passwords
- requiring a password change at the next sign-in

## Why this matters

This lab connects Active Directory group administration to two practical concepts:

- **group-based access management** — manage access through groups instead of assigning permissions individually
- **least privilege** — delegate only the administrative capability required for a specific scope

## Skills demonstrated

- Active Directory security-group administration
- Nested group membership
- PowerShell-based membership management
- Organizational Unit delegation
- Password-management delegation
- Least-privilege administration

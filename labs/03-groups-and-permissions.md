
# Active Directory Security Groups and Delegated Administration

## Overview

Created and managed Active Directory security groups to organize user accounts, simplify membership management, and delegate limited administrative permissions.

## Work Completed

 Created security groups for Sydney, Melbourne, and Brisbane contractor accounts
- Added each contractor account to its matching location-based group
- Created `GG_Australia_Contractors` to manage all Australian contractor groups together
- Nested the Sydney, Melbourne, and Brisbane contractor groups inside `GG_Australia_Contractors`
- Created `GG_Bulk_Users` for PowerShell-provisioned accounts
- Used PowerShell to add accounts from the `_USERS` Organizational Unit to `GG_Bulk_Users`
- Created `Sydney Administrators`, `Melbourne Administrators`, and `Brisbane Administrators`
- Added each contractor account to its matching city administrator group
- Added all three contractor accounts to the built-in `Protected Users` group
- Delegated password-reset and forced password-change permissions over each matching city Organizational Unit


## Contractor Group Structure

The manually created contractor accounts were organized into location-based security groups.

```
GG_Australia_Contractors
├── GG_Sydney_Contractors
│   └── SydneyContractor
├── GG_Melbourne_Contractors
│   └── MelbourneContractor
└── GG_Brisbane_Contractors
    └── BrisbaneContractor
```
## PowerShell Group Assignment

PowerShell was used to add the user accounts located directly inside the `_USERS` Organizational Unit to the `GG_Bulk_Users` security group.

```powershell
# Loads the Active Directory PowerShell commands
Import-Module ActiveDirectory

# Gets all user accounts directly inside the _USERS OU
$Users = Get-ADUser `
    -SearchBase "OU=_USERS,DC=domian,DC=local" `
    -SearchScope OneLevel `
    -Filter *

# Adds the accounts to the GG_Bulk_Users security group
Add-ADGroupMember `
    -Identity "GG_Bulk_Users" `
    -Members $Users
#Display Successful user addition
$Users.Count

```

```
# Delegated Administration
    The delegated permissions allowed group members to:
    Reset user passwords
    Require a password change at the next sign-in
Sydney Administrators
└── SydneyContractor

Melbourne Administrators
└── MelbourneContractor

Brisbane Administrators
└── BrisbaneContractor
```

## Skills Demonstrated

* Active Directory security-group administration
* User and group membership management
* PowerShell group assignment
* Nested security groups
* Organizational Unit delegation
* Password-management delegation
* Least-privilege administration

## Screenshots

### Bulk User Group Membership

Bulk-created accounts were added to the `GG_Bulk_Users` security group.

![Bulk user group membership](/Screenshots/bulk-user-group-membership.jpg)

### Contractor Security Groups

Contractor accounts were organized using location-based security groups.

![Contractor security groups](/Screenshots/contractor-security-groups.jpg)

### Nested Group Membership

Location-based contractor groups were added to a broader contractor security group.

![Nested contractor groups](/Screenshots/nested-contractor-groups.jpg)

### Delegated Sydney Administration

Limited password-management permissions were delegated for the Sydney Organizational Unit.

![Sydney delegated administration](/Screenshots/sydney-delegated-administration.jpg)



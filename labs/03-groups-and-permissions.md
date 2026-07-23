
# Active Directory Security Groups and Delegated Administration

## Overview

Created and managed Active Directory security groups to organize user accounts, simplify membership management, and delegate limited administrative permissions.

## Work Completed

- Created security groups for bulk-created and location-based user accounts
- Added users to security groups through Active Directory Users and Computers
- Used PowerShell to assign accounts from the `_USERS` Organizational Unit to `GG_Bulk_Users`
- Organized contractor accounts through location-based group membership
- Configured nested group membership for broader contractor management
- Created a delegated administrative group for the Sydney Organizational Unit
- Delegated password-reset and password-change permissions
- Verified user and group membership through Active Directory Users and Computers

## Security Group Management

Security groups were used to manage accounts as collections instead of assigning access or administrative responsibilities directly to individual users.

Location-based contractor groups allowed Sydney, Melbourne, and Brisbane accounts to be managed separately while also supporting broader contractor-group membership.

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
## Delegated Administration

A separate administrative group was configured with limited control over the Sydney Organizational Unit. The delegated permissions allowed authorized members to reset user passwords and require a password change without granting full domain-administrator access.

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



# Active Directory User and OU Management

## Overview

Provisioned and organized Active Directory accounts using PowerShell automation and Active Directory Users and Computers.

## Work Completed

- Automated bulk user creation from a text file
- Generated usernames and user principal names
- Created the `_USERS` Organizational Unit and placed automated accounts inside it
- Created Sydney, Melbourne, and Brisbane Organizational Units
- Created and organized contractor accounts by location
- Configured account expiration and City attributes
- Verified accounts through Active Directory and a custom LDAP search

## Manual User and OU Management

Created SydneyContractor, MelbourneContractor, and BrisbaneContractor and moved each account into its matching Organizational Unit. SydneyContractor was assigned an expiration date, and each contractor received the appropriate City attribute.

## PowerShell User Provisioning

The script created multiple accounts with consistent naming, credentials, and OU placement.

```powershell
Import-Module ActiveDirectory

# Domain and OU information
$DomainPath = "DC=domian,DC=local"
$OUName = "_USERS"
$OUPath = "OU=_USERS,DC=domian,DC=local"

# Prompt for a temporary password
$Password = Read-Host "Enter temporary password" -AsSecureString

# Create the OU if it does not already exist
New-ADOrganizationalUnit `
    -Name $OUName `
    -Path $DomainPath `
    -ErrorAction SilentlyContinue

# Create one account for each name in names.txt
foreach ($Name in Get-Content ".\names.txt") {

    $FirstName, $LastName = $Name -split " "

    $Username = (
        $FirstName.Substring(0, 1) + $LastName
    ).ToLower()

    New-ADUser `
        -Name "$FirstName $LastName" `
        -GivenName $FirstName `
        -Surname $LastName `
        -DisplayName "$FirstName $LastName" `
        -SamAccountName $Username `
        -UserPrincipalName "$Username@domian.local" `
        -Path $OUPath `
        -AccountPassword $Password `
        -Enabled $true

    Write-Host "Created user: $Username"
}
```

## Skills Demonstrated

- Active Directory user administration
- PowerShell user provisioning
- Organizational Unit management
- Account-property configuration
- LDAP attribute searching

## Screenshots

### Bulk-Created User Accounts

The PowerShell-created accounts were placed in the `_USERS` Organizational Unit.

![Bulk-created Active Directory users](/Screenshots/bulk-created-users.jpg)

### Location-Based Users and OUs

Contractor accounts were organized into the Sydney, Melbourne, and Brisbane Organizational Units.

![Location-based users and OUs](/Screenshots/location-users-ous.jpg)

### Account Expiration

SydneyContractor was configured with an account expiration date.

![SydneyContractor account expiration](/Screenshots/sydney-account-expiration.jpg)

### City Attribute Search

A custom LDAP filter located contractor accounts whose City attribute was set to Sydney, Melbourne, or Brisbane.

![Contractor City attribute search](/Screenshots/city-search.jpg)

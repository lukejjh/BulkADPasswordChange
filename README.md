# BulkADPasswordChange
A simple PowerShell script which facilitates bulk user password resets in Active Directory.

## Usage
This script should typically be executed on a domain controller as a domain admin.

1. Open PowerShell as administrator.
2. Run the script (e.g. `.\BulkADPasswordChange.ps1`, `C:\path\to\BulkADPasswordChange.ps1`).
3. Add users and/or groups whose passwords you'd like to reset to the temporary security group. Membership is expanded recursively.
4. Confirm the password changes. This will be previewed to you before changing.

A CSV file with user details and their new passwords will be written to a CSV file in the same directory as this script.

### Examples
Typical usage:
```powershell
.\BulkADPasswordChange.ps1
```

Require password change at next logon:
```powershell
.\BulkADPasswordChange.ps1 -ChangePasswordAtLogon
```

Set the same password for all users (not recommended):
```powershell
.\BulkADPasswordChange.ps1 -Password "CorrectHorseBatteryStaple" -ChangePasswordAtLogon
```

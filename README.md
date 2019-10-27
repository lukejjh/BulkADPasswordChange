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

#### Output
```
PS C:\Scripts> .\BulkADPasswordChange.ps1
Temporary password change group created. Press Enter to open ADUC and add users and/or groups to "PasswordChange-2019-10-26-637076972828943989".

Press Enter when all required members have been added to group.


Name           Username       Password
----           --------       --------
Matt Damon     matt.damon     FunPlateLove2
Alec Baldwin   alec.baldwin   TheNineRude97
George Clooney george.clooney WildZeroBurn88


The above password changes will be made. Results will be exported to a CSV file. Continue? [N/y] y
Results saved to "C:\Scripts\PasswordChange-2019-10-26-637076972828943989.csv".
Done.
```

PasswordChange-2019-10-26-637076972828943989.csv:
```
"Name","Username","Password","Email","MobilePhone","Phone","Office"
"Matt Damon","matt.damon","FunPlateLove2","matt.damon@example.org","0455555555","0755555555","Brisbane"
"Alec Baldwin","alec.baldwin","TheNineRude97","alec.baldwin@example.org","0455555556","0755555556","Paris"
"George Clooney","george.clooney","WildZeroBurn88","george.clooney@example.org","0455555557","0755555558","London"
```

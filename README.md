# mypowershell
My Learnings about Powershell

- [sample-scripts-for-administration](https://docs.microsoft.com/en-us/powershell/scripting/samples/sample-scripts-for-administration?view=powershell-7)
- [Great Powershell Articles](https://sid-500.com/)

1. Get Active Driectory Groups attached to useraccount
```ps1
Get-ADPrincipalGroupMembership username | select Name | Where-Object {$_.name -like '*pattern*'} | Sort Name
```

2. Get Members in AD Group
```ps1
Get-ADGroupMember -Identity "JWTCVPSNMID01_Admins" |Where-Object { $_.objectClass -eq 'user' } |
Get-ADUser -Properties * | Select SamAccountName,GivenName,Surname
```

- Script to Read from file list of Groups and display members in each:
```ps1
Get-Content "C:\temp\AD_Groups.txt" | ForEach-Object {
 Write-Host "Members of AD Group ::  $_"
 Get-ADGroupMember -Identity $_ |Where-Object { $_.objectClass -eq 'user' } |Get-ADUser -Properties * | Select SamAccountName,GivenName,Surname
 Write-Host ""
 }
```

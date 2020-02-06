# mypowershell
My Learnings about Powershell

-[sample-scripts-for-administration](https://docs.microsoft.com/en-us/powershell/scripting/samples/sample-scripts-for-administration?view=powershell-7)

1. Get Active Driectory Groups attached to useraccount
```ps1
Get-ADPrincipalGroupMembership username | select Name | Where-Object {$_.name -like '*pattern*'} | Sort Name
```

2. Get Members in AD Group
```ps1
Get-ADGroupMember -Identity "JWTCVPSNMID01_Admins" |Where-Object { $_.objectClass -eq 'user' } |
Get-ADUser -Properties * | Select SamAccountName,GivenName,Surname
```



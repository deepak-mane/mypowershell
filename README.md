# mypowershell
My Learnings about Powershell


1. Get Active Driectory Groups attached to useraccount
```ps1
Get-ADPrincipalGroupMembership username | select Name | Where-Object {$_.name -like '*pattern*'} | Sort Name
```

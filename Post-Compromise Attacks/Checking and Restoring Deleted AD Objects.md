```JavaScript
Get-ADObject -Filter 'isDeleted -eq $true' -IncludeDeletedObjects -Properties * | Select-Object Name, DistinguishedName, ObjectClass, WhenChanged
```
  
- Get-ADObject -Filter 'isDeleted -eq $true' -IncludeDeletedObjects
  
  
- Restore-ADObject -Identitiy <GUID>
    
    - get the GUID through the filter command above
    
![[../assets/Checking and Restoring Deleted AD Objects/image 248.png|image 248.png]]
- GUID is the string starting with 1c6b…
  
![[../assets/Checking and Restoring Deleted AD Objects/image 1 179.png|image 1 179.png]]
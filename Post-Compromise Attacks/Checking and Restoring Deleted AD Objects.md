```JavaScript
Get-ADObject -Filter 'isDeleted -eq $true' -IncludeDeletedObjects -Properties * | Select-Object Name, DistinguishedName, ObjectClass, WhenChanged
```
  
- Get-ADObject -Filter 'isDeleted -eq $true' -IncludeDeletedObjects
  
  
- Restore-ADObject -Identitiy <GUID>
    
    - get the GUID through the filter command above
    
![image 248.png](../assets/Checking%20and%20Restoring%20Deleted%20AD%20Objects/image%20248.png)
- GUID is the string starting with 1c6b…
  
![image 1 179.png](../assets/Checking%20and%20Restoring%20Deleted%20AD%20Objects/image%201%20179.png)
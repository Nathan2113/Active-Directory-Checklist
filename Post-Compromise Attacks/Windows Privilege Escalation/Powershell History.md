In HTB Resolute - the powershell history was a hidden directory in C
- dir -force to see hidden directories
  
to get history location of current powershell session
```JavaScript
(Get-PSReadlineOption).HistorySavePath
```
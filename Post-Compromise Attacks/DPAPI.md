WinPEAS can show DPAPI master keys and credential files for a user
![[/image 18 17.png|image 18 17.png]]
  
with this information, we can copy that information over to our machine and crack the password offline
- copy the masterkey file and credfile over to host
    
    - make sure to copy the Enterprise Credential File
    
  
![[../assets/DPAPI/image 249.png|image 249.png]]
- get the SID for the user (we’ll need it later)
- can also run the following command in powershell to get the user SID’s
    
    - Get-ADUser -Filter * -Properties SID | Select-Object Name, SID
    
  
with the copied files, user SID, and their password, we can get the master key for the encrypted blob
![[../assets/DPAPI/image 1 180.png|image 1 180.png]]
- impacket-dpapi masterkey -file <file> -sid '<sid>’ -password <pass>
  
  
with the decrypted key in the output, we can now decrypt to get the user password
![[../assets/DPAPI/image 2 154.png|image 2 154.png]]
- impacket-dpapi credential -f <file> -key <key>
    
    - the file will be the base64 file copied (for some reason)
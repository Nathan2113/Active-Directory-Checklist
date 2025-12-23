also try to use domain before username if it’s not working
smbclient \\\\<IP>\\<share> -U <DOMAIN>\<user>
  
anonymous login
- smbclient -L \\<IP> -N
    
    - list anonymous shares
    
![[/image 226.png|image 226.png]]
  
List SMB version
nmap -p445 <IP> —script smb-protocols
  
check for vulnerabilities with nmap
- “nmap —script smb-vuln* -p 139,445 <IP>”
  
log into smb using a hash (NT)
- smbclient \\\\<IP>\\<share> -U <user> —pw-nt-hash ‘<hash>’
![[../assets/SMB Client/image 1 164.png|image 1 164.png]]
  
nmap for checking for eternal blue (SMBv1)  
`nmap -p445 --script smb-vuln-ms17-010 <target>`
  
smbmap -H <IP>
- shows what shares we have access to
- not sure if it’s better than crackmapexec or not
  
smbclient \\<IP>\<share> -c ‘recurse;ls’
- lists all files in the SMB share
  
![[../assets/SMB Client/image 2 144.png|image 2 144.png]]
- these policies could be useful
    
    - when looking at the policies, if any of them have a different date you could find Groups.xml in there
    
![[../assets/SMB Client/image 3 128.png|image 3 128.png]]
- could show user information (like hashes)
  
![[../assets/SMB Client/image 4 115.png|image 4 115.png]]
- Groups.xml that is in the policies folder might have info as well
![[../assets/SMB Client/image 5 111.png|image 5 111.png]]
- user is at name=”<DOMAIN\<user>”
    
    - the user in the picture above is “SVC_TGS”
        
        - SVC_TGS is the ticket granting service
        
    
- free password in the Groups.xml as well
    
    - this password is the group policies hash
    
- to decrypt the group policies hash
    
    - gpp-decrypt <hash>
    
![[../assets/SMB Client/image 6 99.png|image 6 99.png]]
- if you get a user this way, remember to check SMB shares
  
when authenticating through kerberos, crackmap and and smbclient may not work, so use the impacket equivalent
![[../assets/SMB Client/image 7 95.png|image 7 95.png]]
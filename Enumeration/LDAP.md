LDAP
- crackmapexec ldap <IP> -M ldap-signing
    
    - gives info about ldap — more specifically, if signing is enforced
    
- nmap -n -sV --script "ldap* and not brute" <IP> \#Using anonymous credentials
- ldapsearch -x -H ldap://<IP> -D ‘’ -w ‘’ -b “DC=<1_SUBDOMAIN>,DC=<DOMAIN>”
    
    - gives more ldap information, can be grepped with “user*” to get users
        
        - can then use this to potentially get user spns for pre-auth users
        
    
- can also try
    
    - ldapsearch -H ldap://<IP> -x -b ”DC=<DOMAIN>,DC=<DOMAIN>
        
        - i.e. -b ”DC=htb,DC=local”
        
        - ldapsearch -x -H ldap://<IP> -D ‘’ -w ‘’ -b “DC=<DOMAIN>,DC=<DOMAIN>” | grep user*
        
    
    - ldapsearch -H ldap://<IP> -x -b “DC=<DOMAIN>,DC=<DOMAIN>” ‘(objectClass=User)’ “sAMAccountName” | grep sAMAccountName
        
        - returns all users in the domain (sometimes ldap and rpc return different users so check both
        
        - when doing this the output is going to have a lot of unecessary info
            
            - put it into a txt file → run “cat user.txt | awk ‘{print $2}’” to get just the users
            
        
    
- nmap -p 389 --script ldap-search -Pn <IP>
- getting user information
    
    - ldapsearch -h <IP> -x -b “DC=<DOMAIN>,DC=<DOMAIN>” ‘(objectClass=person)’ > ldap-people
    
```JavaScript
ldapsearch -H ldap://<IP> -x -b "DC=<DOMAIN>,DC=<DOMAIN>" '(objectClass=person)' > ldap-people.txt
```
  
if you see the following, the machine doesn’t allow anonymous binds
![[../assets/LDAP/image 227.png|image 227.png]]
  
windapsearch
- need to look into
- automates LDAP queries
[[Queries]]
# SharpHound
if on Windows machine, here is how to get bloodhound info
```JavaScript
.\SharpHound.exe -c All --zipfilename <zip_name>
```
  
if you forget your password, add the following to neo4j.conf
- dbms.security.auth_enabled=false
[[Export-08dd1444-22e8-4c73-ac0f-80d7e9ebe484/Active Directory Checklist/Post-Compromise Enumeration/Bloodhound/Setup|Setup]]
![[/Untitled 17.png|Untitled 17.png]]
clicking one of these gives you a graphical view of the query
![[/Untitled 1 5.png|Untitled 1 5.png]]
- can see what targets that user can reach, can disable windows defender, etc
![[/Untitled 2 5.png|Untitled 2 5.png]]
- can mark a user as owned or high value
    
    - marking a user as owned will show you what other paths you can take from that machine
    
  
If you see something like “connecting to LDAP server” in the output when connecting to bloodhound, add the new domain name into /etc/hosts to see all the correct output
![[../assets/Bloodhound/image 233.png|image 233.png]]
- on the bottom ^
  
something good to check once a user has been owned is to check “first degree object control” under node info for that user
![[../assets/Bloodhound/image 1 169.png|image 1 169.png]]
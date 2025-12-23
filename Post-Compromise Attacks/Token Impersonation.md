  
What are the tokens?
- temporary keys that allow you access to a system/network without having to provide creds each time you access a file
    
    - kind of like cookies
    
- Two Types
    
    - Delegate - created for logging into a machine or using RDP
    
    - Impersonate - “non-interactive” such as attacking a network drive or a domain logon script
    
![[/Untitled 24.png|Untitled 24.png]]
- pop a shell and load incognito
![[/Untitled 1 11.png|Untitled 1 11.png]]
- impersonate user
  
![[/Untitled 2 11.png|Untitled 2 11.png]]
![[/Untitled 3 9.png|Untitled 3 9.png]]
- same attack but now we are administrator
  
Attack Replication:
Step 1: Get a shell
![[/Untitled 4 5.png|Untitled 4 5.png]]
![[/Untitled 5 5.png|Untitled 5 5.png]]
![[/Untitled 6 3.png|Untitled 6 3.png]]
  
we are currently authority\system
![[/Untitled 7 2.png|Untitled 7 2.png]]
  
Step 2: load incognito
![[/Untitled 8 2.png|Untitled 8 2.png]]
  
Step 3: list users you can impersonate
- “list_tokens -u”
![[/Untitled 9 2.png|Untitled 9 2.png]]
  
Step 4: Impersonate
![[/Untitled 10 2.png|Untitled 10 2.png]]
![[/Untitled 11 2.png|Untitled 11 2.png]]
- to revert back do “rev2self”
![[/Untitled 12 2.png|Untitled 12 2.png]]
- if an admin has logged in, you can see them with “list_tokens -u” as well
    
    - can be available if the user switched accounts on the computer instead of logging out completely
    
![[/Untitled 13 2.png|Untitled 13 2.png]]
- impersonating administrator
![[/Untitled 14 2.png|Untitled 14 2.png]]
- if you are impersonating an administrator, you can create new users with
    
    - “net user /add username password /domain (type “domain” not the domain name)
    
    ![[/Untitled 15 2.png|Untitled 15 2.png]]
    
    - then we can escalate the new user to administrator with
        
        - “net group “Domain Admins” username /ADD /DOMAIN
        
        ![[/Untitled 16 2.png|Untitled 16 2.png]]
        
    
  
POC: using secretsdump.py with the new user on the domain controller
![[/Untitled 17 2.png|Untitled 17 2.png]]
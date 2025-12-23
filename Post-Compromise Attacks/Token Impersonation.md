  
What are the tokens?
- temporary keys that allow you access to a system/network without having to provide creds each time you access a file
    
    - kind of like cookies
    
- Two Types
    
    - Delegate - created for logging into a machine or using RDP
    
    - Impersonate - “non-interactive” such as attacking a network drive or a domain logon script
    
![Untitled 24.png](/Untitled%2024.png)
- pop a shell and load incognito
![Untitled 1 11.png](/Untitled%201%2011.png)
- impersonate user
  
![Untitled 2 11.png](/Untitled%202%2011.png)
![Untitled 3 9.png](/Untitled%203%209.png)
- same attack but now we are administrator
  
Attack Replication:
Step 1: Get a shell
![Untitled 4 5.png](/Untitled%204%205.png)
![Untitled 5 5.png](/Untitled%205%205.png)
![Untitled 6 3.png](/Untitled%206%203.png)
  
we are currently authority\system
![Untitled 7 2.png](/Untitled%207%202.png)
  
Step 2: load incognito
![Untitled 8 2.png](/Untitled%208%202.png)
  
Step 3: list users you can impersonate
- “list_tokens -u”
![Untitled 9 2.png](/Untitled%209%202.png)
  
Step 4: Impersonate
![Untitled 10 2.png](/Untitled%2010%202.png)
![Untitled 11 2.png](/Untitled%2011%202.png)
- to revert back do “rev2self”
![Untitled 12 2.png](/Untitled%2012%202.png)
- if an admin has logged in, you can see them with “list_tokens -u” as well
    
    - can be available if the user switched accounts on the computer instead of logging out completely
    
![Untitled 13 2.png](/Untitled%2013%202.png)
- impersonating administrator
![Untitled 14 2.png](/Untitled%2014%202.png)
- if you are impersonating an administrator, you can create new users with
    
    - “net user /add username password /domain (type “domain” not the domain name)
    
    ![Untitled 15 2.png](/Untitled%2015%202.png)
    
    - then we can escalate the new user to administrator with
        
        - “net group “Domain Admins” username /ADD /DOMAIN
        
        ![Untitled 16 2.png](/Untitled%2016%202.png)
        
    
  
POC: using secretsdump.py with the new user on the domain controller
![Untitled 17 2.png](/Untitled%2017%202.png)
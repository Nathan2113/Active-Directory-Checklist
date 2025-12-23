Domain Controllers will pull data from other domains if they fail to get the data they need
- this way if a user tries to get info from DC1 and it fails DC2 will get them the information
  
The attack is essentially telling other domain controllers to send you the information from the other DC’s
  
A user needs 3 permissions in order to get the NTDS.dit file
- DS-Replication-Get-Changes
- DS-Replication-Get-Changes-All
- DS-Replication-Get-Changes-In-Filtered-Set
- The following groups have this access by default
    
    - administrators
    
    - domain admins
    
    - enterprise admins
    
    - domain controller
    
  
To perform a DcSync attack, we may need to get a user permission to do so first
- a DcSync attack is basically a [secretsdump.py](http://secretsdump.py) attack
  
If a user is part of the “Windows Exchange Permissions” group, then they have WriteDacl permissions over the domain, meaning that user can give a user DcSync permissions
- first, set up powerview on an http server
![image 254.png](../assets/DC%20Sync%20Attack/image%20254.png)
![image 1 184.png](../assets/DC%20Sync%20Attack/image%201%20184.png)
then use [secretsdump.py](http://secretsdump.py) to dump NTDS.dit with the new user’s information
- in the case above, the new user info is “john:abc123!”
![image 2 158.png](../assets/DC%20Sync%20Attack/image%202%20158.png)
```JavaScript
secretsdump.py '<user>:<pass>@<IP>'
--just-dc-ntlm to dump NT hashes
```
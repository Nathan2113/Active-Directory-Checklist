If there are extra computers, they might be able to read the gmsa password of the gmsa account
![image 239.png](../assets/GMSA/image%20239.png)
- The computer is FS01 and the user is GMSA01$
- will need to get the TGT of the domain computer
    
    - im assuming the password for domain computers is the same as the name of the computer itself
        
        - i.e. FS01$:fs01
        
    
  
![image 1 173.png](../assets/GMSA/image%201%20173.png)
  
export the ccache
![image 2 149.png](../assets/GMSA/image%202%20149.png)
  
use bloodyAD to get GMSA password
- bloodyAD --host <NetBIOS> -d <DOMAIN> -k get object 'GMSA01$' --attr msDS-ManagedPassword
    
    - GMSA01$ may be different depending on the name of the account
    
![image 3 132.png](../assets/GMSA/image%203%20132.png)
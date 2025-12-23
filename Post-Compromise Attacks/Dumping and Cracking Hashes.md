  
secretsdump.py with a username and password
![Untitled 22.png](/Untitled%2022.png)
- in the SAM hashes, the guest and WDAGUtility account do NOT matter
- also worth trying to crack the hashes at the bottom “MARVEL.LOCAL/Administrator:$…”
  
running secretsdump.py with a hash
![Untitled 1 9.png](/Untitled%201%209.png)
  
to crack one of these hashes, all you need is the NT portion, not the LM portion
![Untitled 2 9.png](/Untitled%202%209.png)
  
cracking NTLM hash with hashcat
- -m 1000
![Untitled 3 7.png](/Untitled%203%207.png)
  
  
running [secretsdump.py](http://secretsdump.py) with SAM and SYSTEM
- set up smb server
![image 245.png](../assets/Dumping%20and%20Cracking%20Hashes/image%20245.png)
- copy the SAM and SYSTEM and put them into the share
    
    - change IP to yours
    
![image 1 177.png](../assets/Dumping%20and%20Cracking%20Hashes/image%201%20177.png)
- run [secretsdump.py](http://secretsdump.py) on your kali
![image 2 153.png](../assets/Dumping%20and%20Cracking%20Hashes/image%202%20153.png)
- get money
![image 3 135.png](../assets/Dumping%20and%20Cracking%20Hashes/image%203%20135.png)
- crack those hashes
![image 4 118.png](../assets/Dumping%20and%20Cracking%20Hashes/image%204%20118.png)
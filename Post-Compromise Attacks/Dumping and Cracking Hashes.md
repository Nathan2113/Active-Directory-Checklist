  
secretsdump.py with a username and password
![[/Untitled 22.png|Untitled 22.png]]
- in the SAM hashes, the guest and WDAGUtility account do NOT matter
- also worth trying to crack the hashes at the bottom “MARVEL.LOCAL/Administrator:$…”
  
running secretsdump.py with a hash
![[/Untitled 1 9.png|Untitled 1 9.png]]
  
to crack one of these hashes, all you need is the NT portion, not the LM portion
![[/Untitled 2 9.png|Untitled 2 9.png]]
  
cracking NTLM hash with hashcat
- -m 1000
![[/Untitled 3 7.png|Untitled 3 7.png]]
  
  
running [secretsdump.py](http://secretsdump.py) with SAM and SYSTEM
- set up smb server
![[../assets/Dumping and Cracking Hashes/image 245.png|image 245.png]]
- copy the SAM and SYSTEM and put them into the share
    
    - change IP to yours
    
![[../assets/Dumping and Cracking Hashes/image 1 177.png|image 1 177.png]]
- run [secretsdump.py](http://secretsdump.py) on your kali
![[../assets/Dumping and Cracking Hashes/image 2 153.png|image 2 153.png]]
- get money
![[../assets/Dumping and Cracking Hashes/image 3 135.png|image 3 135.png]]
- crack those hashes
![[../assets/Dumping and Cracking Hashes/image 4 118.png|image 4 118.png]]
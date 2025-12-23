rpcclient
- anonymous login with — rpcclient -N -U "" domain.local
    
    - can apparently also just do
        
        - rpcclient -U ‘’ -N <IP> on domain controller
        
    
    - once logged in, type “enumdomusers” and “enumdomgroups”
    
- can log in with creds with — rpcclient -U <user%pass> <IP>
  
rpcinfo
- rpcinfo -f <IP>
    
    - returns all available rpc services available
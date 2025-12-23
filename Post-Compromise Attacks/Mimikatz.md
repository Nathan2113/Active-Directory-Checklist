[[Backdoor w- mimikatz]]
  
WIll get picked up by any sort of antivirus
- to fully utilize it, you have to obfuscate it or disable antivirus
it can do the following:
- steal credentials stored in memory
- generate kerberos tickets
- credential dumping
- pass-the-hash
- over-pass-the-hash
- pass-the-ticket
- silver ticket
- golden ticket
  
First thing to do when opening mimikatz
- run “privilege::debug”
    
    - gives permission to run all the attacks we want
    
![[/Untitled 27.png|Untitled 27.png]]
![[/Untitled 1 14.png|Untitled 1 14.png]]
- sekurlsa options
can look for cleartext credentials or NTLM hashes with the dump
![[/Untitled 2 14.png|Untitled 2 14.png]]
- the cleartext above will only show up if there is a network fileshare
![[/Untitled 3 11.png|Untitled 3 11.png]]
- this cleartext doesn’t show up in lsassy or secretsdump, which means that mimikatz does some extra stuff
  
  
dump the sam
- lsadump::sam
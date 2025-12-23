sudo neo4j console - required to use bloodhound
![image 148.png](/image%20148.png)
- running bloodhound will give a link to a localhost port
  
![Untitled 28.png](/Untitled%2028.png)
- log in with
    
    - Username: neo4j
    
    - Password: neo4j
    
- it will have you change the password (neo4j1) (or neo4j!)
now type “sudo bloodhound” into the console and bloodhound will open
![Untitled 1 15.png](/Untitled%201%2015.png)
log in to get a blank screen
![Untitled 2 15.png](/Untitled%202%2015.png)
now set up the ingestor
![Untitled 3 12.png](/Untitled%203%2012.png)
sudo bloodhound-python -d <DOMAIN> -u <user> -p <pass> -ns <IP> -c all
- -ns is nameserver (IP)
- -c is what to collect (all)
- if authenticating with kerberos (i.e. TGT’s), then do the exact same command but add the -k flag
running this command gives you some information
![Untitled 4 7.png](/Untitled%204%207.png)
also creates new files
![Untitled 5 7.png](/Untitled%205%207.png)
go to browser interface and upload the data using the button on the right
![Untitled 6 5.png](/Untitled%206%205.png)
give it the folder with all of the loot
![Untitled 7 3.png](/Untitled%207%203.png)
  
  
  
if you get a postgres mismatch error on first startup
```JavaScript
sudo -u postgres psql
ALTER DATABASE template1 REFRESH COLLATION VERSION;
ALTER DATABASE postgres REFRESH COLLATION VERSION;
```
- follow steps given from output after running bloodhound again
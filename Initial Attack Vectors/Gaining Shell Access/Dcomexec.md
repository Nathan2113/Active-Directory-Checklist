remotely execute commands through DCOM (Distributed Component Object Model) and RPC (Remote Procedure Call)
  
What you need
- username
- password
- domain
- IP
  
Example command:
- [dcomexec.py](http://dcomexec.py) -object MMC20 <DOMAIN>/<user>:<pass>@<IP>
  
[https://book.hacktricks.xyz/windows-hardening/lateral-movement/dcom-exec](https://book.hacktricks.xyz/windows-hardening/lateral-movement/dcom-exec)
```JavaScript
enum4linux -a <IP>
```
- will give all users among other information
- runs with anything that has rpc
  
uses the following enumeration tools
- nmblookup
- nbtstat
- net
- rpcclient
- smbclient
  
enum4linux-ng
- rewrite of enum4linux in python
- has additional features
    
    - can export data as YAML or JSON
    
```JavaScript
enum4linux-ng -P <IP> -oA <filename>
```
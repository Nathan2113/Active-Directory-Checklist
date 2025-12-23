[https://github.com/p0dalirius/pyLAPS](https://github.com/p0dalirius/pyLAPS)
  
```JavaScript
python3 pyLAPS.py --action get -d "<DOMAIN>" -u "<DOMAIN>/<user>" -p "<pass>"
```
- if it’s cross domain, just put your user’s valid domain credentials are (check below)
![image 409.png](../../assets/ReadLAPS/image%20409.png)
- petyer.baelish is part of sevenkingdoms.local, but the LAPS password was for a workstation in essos.local (the attack still worked)
![image 409.png](/image%20409.png)
- password dumped from pyLAPS isn’t working, but the attack executed successfully
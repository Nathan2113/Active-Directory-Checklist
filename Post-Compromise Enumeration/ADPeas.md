https://github.com/61106960/adPEAS
  
once in poweshell instance, upload adPEAS.ps1
![image 241.png](../assets/ADPeas/image%20241.png)
  
run the following commands to run AD enumeration
- Import-Module ./adPEAS.ps1
- Invoke-adPEAS | Out-File output.txt
![image 1 175.png](../assets/ADPeas/image%201%20175.png)
  
look for anything of note, like emily.oscars being part of the Backup Operators group
![image 2 151.png](../assets/ADPeas/image%202%20151.png)
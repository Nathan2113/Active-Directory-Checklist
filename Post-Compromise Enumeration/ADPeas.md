https://github.com/61106960/adPEAS
  
once in poweshell instance, upload adPEAS.ps1
![[../assets/ADPeas/image 241.png|image 241.png]]
  
run the following commands to run AD enumeration
- Import-Module ./adPEAS.ps1
- Invoke-adPEAS | Out-File output.txt
![[../assets/ADPeas/image 1 175.png|image 1 175.png]]
  
look for anything of note, like emily.oscars being part of the Backup Operators group
![[../assets/ADPeas/image 2 151.png|image 2 151.png]]
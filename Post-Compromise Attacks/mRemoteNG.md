used for managing remote connections
- if on a Windows machine, check Program Files and Program Files (x86) for mRemoteNG
  
![image 251.png](../assets/mRemoteNG/image%20251.png)
- if the computer has mRemoteNG, we can find the user passwords stored
  
go to the user folder for the user that you have, then go to the following folder to find confCons.xml
![image 1 182.png](../assets/mRemoteNG/image%201%20182.png)
  
cat that file to find the passwords for users for mRemoteNG
![image 2 156.png](../assets/mRemoteNG/image%202%20156.png)
- Password is found ater “Password=…”
  
once you have the password, get the decryption script from this github
https://github.com/kmahyyg/mremoteng-decrypt
  
run the decryption script to get the password
![image 3 137.png](../assets/mRemoteNG/image%203%20137.png)
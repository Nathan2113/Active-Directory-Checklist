When you get an error where the SMB isn’t part of the Kerberos service database, you need to get the cifs service ticket to connect to the SMB
- process shown below
  
impacket-getST -k -no-pass -dc-ip <IP> -spn cifs/<DC> <DOMAIN>/<user>
- DC is something like dc01.voleur.htb
- can be used if the kerberos server is not found in the database
    
    - used in voleur because we got the “STATUS_NOT_SUPPORTED” error on smb
    
  
can now try authenticating to smb
- impacket-smbclient -k <DOMAIN>/<user>@<DC>
    
    - DC is something like dc01.voleur.htb
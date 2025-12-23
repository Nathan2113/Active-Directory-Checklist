Allows a user to perform actions as another user
- i.e. some low level user can impersonate NT\Authority
  
machines with the SeImpersonatePrivilege enabled on a user are typically vulnerable to the potato exploits (juicy, lonely, rotten)
[https://support.plesk.com/hc/en-us/articles/12376963995287-Microsoft-Windows-SeImpersonatePrivilege-Local-Privilege-Escalation](https://support.plesk.com/hc/en-us/articles/12376963995287-Microsoft-Windows-SeImpersonatePrivilege-Local-Privilege-Escalation)
  
if the machine is a 2003 Windows Server, use Charrasco
https://github.com/Re4son/Churrasco/
[[Privilege Escalation with Churrasco]]
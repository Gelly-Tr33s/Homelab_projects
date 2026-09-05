# Overview 
Now that I have Active Directory installed, I'm now going to be configuring the DNS and DHCP server. The DNS is what connects the other computers to the server and the DHCP is
the tool we need to automatically assign an IP address to client computers.

## Checking DNS
First, I looked up the DNS IP address just to make sure we are still using the right IP. I used the following commands:
```bash
nslookup mydomain.local
nslookup myDomainControllerHostname
```
This outputs the same static IP used earlier, it is the correct DNS used.            
<img width="530" height="447" alt="nslookup" src="https://github.com/user-attachments/assets/129fedde-9423-4c9a-a956-7c32ed9fd822" />

## DHCP Server installation  
Now that the DNS is ok, I installed the DHCP server in the Windows Server:      
<img width="972" height="692" alt="DHCP-installation" src="https://github.com/user-attachments/assets/84e82d37-12be-4b7c-9f13-bcab679e79da" />     

Next, I assigned the range of IP addresses to be used:    \
<img width="631" height="457" alt="AssigningDHCP-Scope" src="https://github.com/user-attachments/assets/4ef00f4b-24a9-457c-94e3-8ed889e456d7" />     
<img width="930" height="591" alt="DHCP-IPSCOPE" src="https://github.com/user-attachments/assets/8be4a85f-7f9c-4672-b671-83c7ddd20852" />     

The IP address range configuration is done and we can see the range here:     
<img width="816" height="527" alt="DHCP-installed" src="https://github.com/user-attachments/assets/d5e9b06b-76e7-4b30-b25e-f270e6131bbe" />

Next, will attempt to connect a Win11 VM to the server.


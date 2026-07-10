## Configuring SSH

Now, I am going to configure SSH (secure shell). This is a network protocol that allows the server to be accessed remotely and securely. Before, there was Telnet. It is basically the same as SSH except
that it transmits credentials in plain text, making it very unsecure for today's standards. So SSH makes this access more secure by encrypting the credentials transmitted.

First, I installed the SSH on the server using
```md
sudo apt update && sudo apt install ssh
```
Here I can see the status of the ssh server (I haven't started this one)  

<img width="692" height="132" alt="UBS-ssh-installed" src="https://github.com/user-attachments/assets/49c2d0b8-c499-4719-bdf2-c23f7e1762a4" />

## Next, the setup.

I started the server using
```md
sudo systemctl start ssh
```
and checked the status using
```md
sudo systemctl status ssh
```
And here, we can see that it's running (note to self: spelling is very important)    
<img width="347" height="125" alt="UBS-ssh-start" src="https://github.com/user-attachments/assets/43439821-6780-4a5a-9470-79b4eb179051" />

Now that setup, I needed to make the server connect to another machine. This involves using the Internal Network setting in VirtualBox. This keeps both server and client machine isolated from the internet. Making it safe for lab experiments.
    
Here, the client machine was able to reach the server.   
<img width="607" height="297" alt="UBS-client-to-server-ping" src="https://github.com/user-attachments/assets/be69e6c2-7517-4718-a0a0-a97576329274" />


So, what I did is:
1. Set up the server with two network adapters (one for NAT which allows the server to connect to the internet for updating packages, other is an internal network which makes a private network).     
<img width="1297" height="107" alt="UBS-networksetup" src="https://github.com/user-attachments/assets/472b1f0a-70b4-4e0c-9fd2-6ff59412478d" />

2. Set up the client VM (which is the Kali VM) with one adapter which is an internal network adapter with the same name that I setup in the VirtualBox settings.
<img width="701" height="266" alt="kali-network-setup" src="https://github.com/user-attachments/assets/3c8dbd94-202f-4ee9-bbc3-505581b66707" />

3. On each machine, I assigned their own IP address so that they can reach each other in this isolated setup.
```md
sudo systemctl status ssh
```

With that done, I proceed to making ssh configurations. I used hardening settings such as
```md
Port 22
PasswordAuthentication yes (will try keys later)
LoginGraceTime 1m
PermitRootLogin no (very important to avoid root access to the server)
ListenAddress [internal network IP] (to isolate ssh from the internet)
```

After making these configurations, I restarted the service and I encountered a problem: 
When I checked if the server is listening to only the internal network address, it turned out its still listening to all IPs (0.0.0.0:22) even if I set the config file to only listen to my internal network address. I've done research and it turned out that newer versions of Ubuntu have this thing called sockets or systemd socket activation which improve startup behavior and resource usage. But in my case I dont need it, so I disabled it.

Upon disabling it, it is now listening only in my internal private network.  
<img width="437" height="60" alt="UBS-ssh-listenaddr" src="https://github.com/user-attachments/assets/33144d2a-a360-424e-8f21-bab601dbb287" />

With those problems solved, I tried to connect the client to the server using:  
```md
ssh [serverUsername]@[serverIPaddr]
```
then typed in the password of the server user and I'm now controlling the server from the client side:  
<img width="696" height="322" alt="kali-client-to-server" src="https://github.com/user-attachments/assets/ad1acfa7-c14a-4fca-9542-e98f1b353422" />

Next, I'll use keys for authentication, making the ssh access more secure.







# Configuring My Server's Host Name
While using SSH with key authentication is a convenient way to connect to my server, I still experience a little bit of inconvenience trying to connect to it. 
Specifically when I need to type my server's IP address. So I would configure the server's name into a simpler name instead of having to type the IP for better usability.

## The Setup
First, I checked the current hostname:  
<img width="220" height="66" alt="UBS-hostname" src="https://github.com/user-attachments/assets/3ef14474-300d-441f-8c2e-b5dd2df4bcf5" />         
Right now, this sounds very generic as I used the Ubuntu server as the name. 

To fix that, I changed the hostname locally:   
<img width="468" height="86" alt="UBS-hostname-change" src="https://github.com/user-attachments/assets/e8b8c0d5-15f4-41b6-b85a-d4733d7d0070" />

 After the restart, terminal now uses a simple name:    
 <img width="217" height="52" alt="UBS-hostname-change-verify" src="https://github.com/user-attachments/assets/5a408d0a-fc27-430c-b3d2-fa31d66c5652" />

Next, I installed avahi-daemon to simplify SSH connections by letting the server be addressed using the hostname   
<img width="452" height="67" alt="UBS-avahi-installation" src="https://github.com/user-attachments/assets/1a93635c-f956-481d-b919-29152285ecb7" />     
This verifies that avahi-daemon is working.

## Problem encountered
Next is to verify that I could now SSH into the server using the hostname. Upon checking that however, I encountered a problem:
The client machine could not connect to the server because it is missing. 
<img width="697" height="61" alt="kali-hostnameProblem" src="https://github.com/user-attachments/assets/6f4fd8a9-0e6c-45ba-bcb4-5d1a100aa45d" />

I forgot that I have the SSH service on the server off so I turned it on:   
<img width="347" height="47" alt="UBS-ssh-off" src="https://github.com/user-attachments/assets/700d4f36-1e01-4864-9dc3-39f1e55c1d4f" />

### Problem Discovery

Although `avahi-daemon` was installed and running, the client could not resolve `myhomelab.local`.

### What I did is:

- Verified IP connectivity between the Ubuntu Server and Kali VM.
- Confirmed multicast support on the network interface.
- Verified that Avahi service discovery worked using a manually published test service.
- Determined that the server was not advertising its workstation hostname.

### Root Cause

The following option in `/etc/avahi/avahi-daemon.conf` was disabled:

```ini
publish-workstation=no
```
This means that the server is not advertising it's hostname to other machines in the network. Making connections (especially SSH) not possible using the hostname.
By enabling this, it allows the server to advertise its hostname (myhomelab.local) via Multicast DNS (mDNS), 
enabling other devices on the same local network to discover and resolve the server by hostname instead of IP address.

### Solution
I set the configuration of publish-workstation to "yes" to allow the server to advertise its hostname.     
<img width="195" height="37" alt="UBS-avahi-configSolution" src="https://github.com/user-attachments/assets/67eb0b0f-9274-4a66-b011-db471ee04df1" />          
Afterwards, I restarted the service and confirmed that it advertises its hostname in the network.    
<img width="707" height="93" alt="UBS-avahi-workstation" src="https://github.com/user-attachments/assets/26790d46-29b1-412a-88a2-bd77f4e16eaa" />

## Result
I was now able to SSH in my server using the hostname:     
<img width="267" height="52" alt="Kali-to-UBS-connection-hostname" src="https://github.com/user-attachments/assets/cc6b16dd-c2cc-4290-b81a-fe759b7c1137" />







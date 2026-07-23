# Configure UFW
Today I will be configuring uncomplicated firewall (ufw) in the server. Having a firewall keeps the server safe by having 
every packets inspected before going into the network.

# Setup
I step-up the firewall with the standard rules to keep the server secure.
These rules are:
1. Deny incoming, allow outcoming - This means to deny all incoming unsolicited connections while allowing outgoing traffic. In my case, it allows the server to still
receive updates.          
<img width="408" height="130" alt="UBS-ufwDefault" src="https://github.com/user-attachments/assets/36eea37f-4bb2-4569-9a48-c04a071ffdf7" />             

2. Allow ssh only with the client VM in the internal network. This is important because I ssh into my server using the client VM.      
<img width="732" height="61" alt="UBS-ufwOnlyClient" src="https://github.com/user-attachments/assets/049fe6e7-aaec-47e6-96f0-62e85e08fa17" />      

3. Allow my hostname to be only discovarble in the internal network. This keeps the server only available in the internal network.       
<img width="597" height="32" alt="UBS-ufwOnlyInternalNetwork" src="https://github.com/user-attachments/assets/d5d832fe-70a5-4863-8149-326cd580e2f9" />

With these done, I doubled checked the rules that are applied:      
<img width="467" height="170" alt="UBS-ufwRulescheck" src="https://github.com/user-attachments/assets/8cd9f163-0b7f-432f-8218-53de37945c5f" />

After that, the firewall was working fine until I tried to ssh into the server.

# Problem Encountered:
- I could ssh into the server using the IP address but not the hostname.

## What I investigated:
- The status of avahi-daemon. It is confirmed to be running.

## Problem Discovery:
- On the status of the instance, it was using a different host name, it was using myhomelab-2.local.       
<img width="222" height="45" alt="UBS-avahi-Problem" src="https://github.com/user-attachments/assets/0b13ac3b-686d-4732-8320-8d94ecd645e1" />                
- So it turned out Avahi temporarily detected a hostname conflict and automatically appended `-2` to ensure uniqueness on the network. Hence, a 2 in the hostname.

## Solution:
I restared the daemon to make it use the original hostname and now it is using it:             
<img width="275" height="46" alt="UBS-avahi-ProblemSOLVED" src="https://github.com/user-attachments/assets/c6a0cd4f-5891-4271-83f1-64d850d7d24b" />

# Result
I was now able to ssh into the server with firewalls and using the hostname:   
<img width="533" height="86" alt="UBS-ufwFirewallsuccess" src="https://github.com/user-attachments/assets/f0217b1f-fa5c-4df8-983d-df4fae862d9e" />

## Conclusion
A firewall can help protect a system from malicious packets. It is always recommended
to use default rules such as "deny incoming, allow outgoing". Not only that, we should rules that
also make sure that other functionalities such SSH still works. And lastly, don't forget to double-check
and always make that the configurations are applied (i.e. by restarting the service).






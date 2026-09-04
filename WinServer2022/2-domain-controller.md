# Overview
Before I dive in straight to using Active Directory, I need to configure first the domain controller. The domain controller is the server where we can run the
Active Directory. It authenticate users and provides them the access of whatever they only need.

## Setting up the domain controller
First, I have to change the name of the server into something simple because the server name in my fresh install has random and complex.
<img width="866" height="397" alt="ServerNameChange" src="https://github.com/user-attachments/assets/b26dbd59-0e49-49cd-94c8-68b3d50f04c5" />

Afterwards, I have to assign a static IP address to the domain controller. I use DHCP on it and the IP changes, the devices connected to it will lose access, making users
unable to log in. However, since I am using a virtual environment, I need to be careful in assigning a static IP and network settings in the hypervisor I'm using. I did
discover that VirtualBox has its own DHCP, which means I should use an IP address that is outside the range of VBox's DHCP. 

Here is the range of the DHCP of VBox for reference:
<img width="587" height="288" alt="Vbox-DHCP" src="https://github.com/user-attachments/assets/2f6986e1-af70-4ce6-a35c-f1cd8d9ad95f" />       

With that in mind, I used an IP address that is outside the range:    
<img width="990" height="685" alt="AssigningStaticServerIP" src="https://github.com/user-attachments/assets/0f7f83a3-1177-43c7-abe8-9ce11ee771c0" />

I also adjusted the network settings of the VM before changing the IP. The first adapter is set to host only, which means only the other VMs can communicate with the server.
The second adapter is set to NAT so that the server can still have internet access without needing to interact with the home router directly. I would avoid using bridged-adapter
to prevent misconfigurations to our home router.    
<img width="757" height="127" alt="NetworkSetup" src="https://github.com/user-attachments/assets/bf5ff80e-4b00-4a05-b62b-ea2415b29c3e" />       


## Installing the Active directory
With all the configurations done, I proceeded to install the Active Directory by clicking the "2. Add roles and features". And check the Active Directory Domain Services    
<img width="1045" height="740" alt="InstallingAD" src="https://github.com/user-attachments/assets/a2765cd8-cdd7-4824-9e8d-a21f6329d924" />

Active Directory now installed:   
<img width="337" height="392" alt="ADinstalled" src="https://github.com/user-attachments/assets/66835a5c-b36d-4e16-b51e-4b49fc2ec02d" />

Final step is to promoting the server by assigning a domain name. This is shown in a flag with notifications on it, there I could set the domain name of the server along with
other configurations.
<img width="607" height="112" alt="promotedServer" src="https://github.com/user-attachments/assets/4436d671-cb33-446a-989f-8609faec8b10" />

Next, I will be configuring the DNS 







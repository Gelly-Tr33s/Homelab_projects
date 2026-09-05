# Overview
Now that DNS and DHCP is now configured, I now did one of the big parts of this homelab, adding another user from another computer.

## Making an org group, groups, and users
Before I start creating users, I make groups of accounts which contains the users, and the another group call groups for departments like HR and maintenance.                  
<img width="896" height="671" alt="MakingOrgGroup" src="https://github.com/user-attachments/assets/e82ad814-3f63-4a65-bc2e-31bd7d1ae920" />       

Here is the first user and group I made:    
<img width="905" height="680" alt="Creating1stUser" src="https://github.com/user-attachments/assets/c39e5384-12d4-4e2b-956c-7bc44125c15d" />
<img width="632" height="551" alt="CreatingGroups" src="https://github.com/user-attachments/assets/bf469345-4501-403f-be17-b9123d40b04a" />            

I made two users and two groups for now:      
<img width="642" height="371" alt="Users" src="https://github.com/user-attachments/assets/ae1408f9-4b3b-476b-a1f6-184269da945e" />
<img width="630" height="417" alt="Groups" src="https://github.com/user-attachments/assets/06d31925-1eba-4533-bf0b-87a1daae4206" />

For the account options, I required the user to enter have them change password at the next log in. This allows them to have their password on
their account the first time they log in.                      
<img width="477" height="465" alt="accountOptions" src="https://github.com/user-attachments/assets/a2a22313-17ce-4d29-9f00-43d94522f74c" />

## Windows Client machine perspective:
To have the windows client join in the AD server, I adjusted the IPv4 settings and changed the DNS server address
to the static of the AD server I had:      
<img width="862" height="652" alt="Win11IPv4Setting" src="https://github.com/user-attachments/assets/6bf4b47d-bf0e-4ce7-9223-773a2175545a" />


Afterwards, I went to the system properties and clicked "Change":
<img width="812" height="782" alt="Win11Client" src="https://github.com/user-attachments/assets/7f5f0cdc-cd19-41ea-b2ef-dc06633b6050" />

### Problem encountered and solution done
In the settings however, I encountered a problem. I could not enter the domain name of the server because the option to do so is greyed out.
After a quick research, it turns out that I was using the wrong version of Windows 11, which does not allow joining an Active Directory domain by default.
As a solution, I did a fresh reinstall of Windows 11 pro and I was now to join the AD domain.   

It prompted for the credentials of the Administrator account:    
<img width="920" height="650" alt="Win11NewInstall-Domain" src="https://github.com/user-attachments/assets/aa714fb6-f954-4ea6-8bc9-d10c90fbeb2b" />              

After entering credentials, I was able to join the client machine to the AD server successfully:    
<img width="791" height="607" alt="Win11ClientJoinSuccess" src="https://github.com/user-attachments/assets/24803fd4-3615-4205-bee2-1c90146cd7b7" />            

I could enter the username and password of the user I created:   
<img width="942" height="761" alt="Win11NewClient" src="https://github.com/user-attachments/assets/63b06e24-6da8-441a-8f25-7c4137e20423" />
             
After entering the correct details, it asks for the user to set their own password. The password entered by the client
will stay with them and the admin wouldn't know the password itself. After the password setup, I was able to enter as user in the client machine that is in the AD server:                
<img width="860" height="702" alt="Win11ClientLogInSuccess" src="https://github.com/user-attachments/assets/265305e4-e671-4d5e-921e-f840c799a3c7" />


## Server view of connection done
In the server side, I could now see the name of the computer that joined the server.           
<img width="742" height="396" alt="Win11ClientComputerConnection" src="https://github.com/user-attachments/assets/e1993bb9-aa64-4f82-adaf-1b6223535aa1" />


Next, I will continue to learn Active Directory and Identity management.





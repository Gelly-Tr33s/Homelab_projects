# Overview
While I learned how to set and reset passwords for the clients in the Active Directory, I wondered
what should I do when I (the admin) have forgotten the password in the server? So, today I learned
how to reset the admin password on Windows Server 2022.

## What I did:
First, I have to shutdown the server first and access the Windows Recovery Environment (WinRE) to 
access the command prompt.                                      
<img width="782" height="597" alt="WinRE" src="https://github.com/user-attachments/assets/be16b896-9f13-4c8d-b3c9-bb95d645b2b9" />

After that, I found the boot drive which was the C drive. What I have done here is basically making
the command prompt easily accessible in the login screen by clicking the Ease of Access option in the
bottom right menu of the login screen. 
<img width="452" height="187" alt="utilman" src="https://github.com/user-attachments/assets/73a340db-2947-43ea-a1cf-cd6f5f3d9d7e" />

Next, I exited the command prompt and restarted the server. From the login screen, I clicked the Ease of Access and it led me to
the command prompt right away. I reset the password in there. In my case, I only reset the local account, not the domain controller.
If the domain controller password needed to be reset, I would use the same command but with "/domain" in the end. I entered the new password 
and can confirm that I could log in. This mean that password reset was done successfully.   

Command: 
```bash
net user administrator [password]
```

<img width="932" height="200" alt="Pass_reset" src="https://github.com/user-attachments/assets/13e21483-2168-419b-b9a0-dc33de2e0150" />    
<img width="1005" height="767" alt="AccountAccessed" src="https://github.com/user-attachments/assets/3bbc1743-1e54-49ea-a71a-9bf32ff86c5c" />                                   


## Important thing to do after:
After the reset, I need to revert the utilman settings back to default. I learned that leaving the command prompt accessible in the utilman (Ease of Access)
is a vulnerability that allows malicious actors to gain admin access to command prompt and possibly gain full control when the server was accessed
remotely. With this setting reverted, I could log into the server with the updated password while keeping it secure.                                 
<img width="587" height="342" alt="Revert_Setting_Utilman" src="https://github.com/user-attachments/assets/9f354e13-131f-46cd-a05a-761eb8b20e3e" />



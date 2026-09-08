# Overview
Today I learned permission controls. This involves
- User groups
- Folders

Learning to control permissions is important to prevent unauthorized access which may result into data loss and exfiltration
as well as other malicious activities, keeping systems safe. Aside from security benefits, this also helps organize management
by assigning specific access to specific users only.

## User groups
In this section, I learned to assign users to different groups that I created earlier. I assigned one user to a group.

### How I did it
I right-clicked the selected user -> All tasks -> Add to a group -> typed in the sample group I made earlier (Maintenance) and
clicked "ok".       
<img width="857" height="630" alt="UserAssignedToGroup" src="https://github.com/user-attachments/assets/f7ded7c3-b456-4aa0-8690-e3b878e12a83" />

Once that is done, the user (Jane Doe) should be part of the Maintenance group. To double check, see the properties of the user.                 
<img width="497" height="625" alt="DoubleCheck" src="https://github.com/user-attachments/assets/63f8296a-c53c-4fef-bdc6-11650e670647" />

The user (Jane Doe) should also be a member of the Maintenance group according to the properties of it.     
<img width="495" height="352" alt="DoubleCheckGroup" src="https://github.com/user-attachments/assets/9cab26e3-b39d-40ab-8ce4-3ed3b57a190e" />


## Shared folders via group
Here, I learned to assign a specific folder only to a group I selected. In a security context, this is an example of RBAC (Role-Based Access Control),
wherein permissions to access a resource is tied to only a specific group (or role), giving only the necessary data while restricting
access to other data, especially sensitive ones.

### How I did it
First, I made a shared folder related to the different roles (groups) I made. There is also the target folder (Maintenance) 
which I intend to give user (Jane Doe) access to.            
<img width="865" height="342" alt="SharedFolder" src="https://github.com/user-attachments/assets/5912c2c5-b226-4dad-8ab8-eff01d30be9f" />
<img width="682" height="330" alt="TaregetFolder" src="https://github.com/user-attachments/assets/318aaf7d-9252-4061-8df9-8785bd9be67a" />

Next, I selected the target folder -> Properties -> Sharing -> Advanced Sharing -> Check "Share this folder" -> Permissions
-> Share Permissions. In this homelab setup I used the default group and allowed Full Control. However, in the enterprise environment
the shared access should be more strict.                  
<img width="807" height="565" alt="SharedFolderSetting" src="https://github.com/user-attachments/assets/c170fa1a-af84-49db-b1d2-e94bf3875340" />

And then I added the Maintenance group I made in the AD to the security permissions of the folder.        
<img width="786" height="632" alt="GroupFolderAssignment" src="https://github.com/user-attachments/assets/0a7949db-e920-4729-b74f-1ce105e79f88" />

When I selected the Maintenance group, I gave the group Modify, Read & execute, List folder contents, Read, and Write permissions.
But I did not give them Full control since they do not need it.     
<img width="605" height="647" alt="GroupPermissions" src="https://github.com/user-attachments/assets/27794e9a-6c01-4c48-92d2-f2725d9e370b" />

Here is the Admin permissions in comparison:             
<img width="537" height="602" alt="AdminPermissions" src="https://github.com/user-attachments/assets/53de3ef1-282b-4c44-8c89-70e51a70fc1c" />

Once those settings are done, I now logged in the client (Jane Doe's) computer. However the folder is not there right away.         
<img width="937" height="756" alt="ClientSide" src="https://github.com/user-attachments/assets/60ff0de1-34a0-4426-89c4-ca1f38ad8420" />

To fix this, I right-clicked the Network folder -> Map Network Drive and entered the domain name and the folder that I intend to share earlier and clicked Finish.                
<img width="876" height="670" alt="NetworkFolder" src="https://github.com/user-attachments/assets/909953e6-2a6d-4b7e-bcfe-f0a7fae8a4c9" />

Finally, the client (Jane Doe) has now access to the shared folder:                     
<img width="876" height="670" alt="NetworkFolder" src="https://github.com/user-attachments/assets/38376e0b-71c8-4de7-b040-e6f3d9b44166" />

Since I provided her group write permissions, she can also make folders. The modifications will be also seen in the Admin side.

Client side:                       
<img width="862" height="535" alt="ClientModify" src="https://github.com/user-attachments/assets/efff853b-cb02-49ae-91f8-e1722462f331" />

Admin side:       
<img width="931" height="761" alt="AdminSideChanges" src="https://github.com/user-attachments/assets/3b0f5dc5-3790-47b9-a760-133da3326d76" />

And that is how I was able to learn shared folder permissions in Active Directory. I will continue to explore Active Directory tools and tasks for help desk and system admin tasks.




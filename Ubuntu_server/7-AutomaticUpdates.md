# Automatic Updates

As I said earlier, updating a system especially if its about security updates is important to keep systems safe from possible vulnerabilities.
While updating the system is really simple but having it updated automatically makes it more convenient so today I will configure automatic updates in
the server using unattended upgrades.

## Setup
First I need to install the tool for automatic updates called unattended-upgrades.
```md
sudo apt install unattended-upgrades
```

Upon installing this tool, I discovered that this is already installed by default and is running because it is installed by default.
So checked the main configuration file to make sure that is really getting the updates, which is found in the 20auto-ugprades:
<img width="356" height="312" alt="UBS-unattendedUpgrade" src="https://github.com/user-attachments/assets/f7fa1edc-57f0-430e-92c9-aab7da68d1b8" />           
<img width="367" height="51" alt="UBS-autoupgrades-on" src="https://github.com/user-attachments/assets/492fadb9-2c60-4ee3-8c77-994210d87718" />               
Both settings are on "1" which means that the unattended update and upgrades option is on. If its set to "0", it means it is off. 

Another file to modify is the 50unattended-upgrades, a configuration file for selecting repositories for updates, stopping a repository from getting updates, as well
as settings for behaviors of packages during updates.

One of the settings I modified is the one that fixes an unclean package download if that ever happens.  
<img width="532" height="97" alt="UBS-dpkgBehavior" src="https://github.com/user-attachments/assets/b524d6bf-085e-485d-9626-1a931385381b" />             

Another is setting the reboot time to another time instead of the default which was 2AM. The reason is for less risk of attack. If its left on
the default time, anybody including malicious actors would know that update time and may try to do something before that update in case that there's a
vulnerability in a system before.
<img width="562" height="77" alt="UBS-updateTime" src="https://github.com/user-attachments/assets/a69d0519-1621-46f8-8a79-f0c2e3ca9e76" />

Now with these settings done, I restared the tool to apply these changes to the configurations.





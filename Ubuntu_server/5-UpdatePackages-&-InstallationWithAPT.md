# Updating Packages

Updating packages involves getting the latest software packages from repositories. This usually involves security patches and configuration updates. 
It is a commonly-known fact that we should always update software to keep our systems updated and secured. Not updating means a risk of vulnerabilities or bugs that
are not patched. This is especially true when we use software that no longer provides updates or has reached EOL (End-of-Life).

Fortunately, updating in Linux is quite simple. We simply use these commands  
```md
sudo apt update
```
which gets the updates packages and
```md
sudo apt upgrade
```
which applies the updates to our existing systems.

Here is getting the updated packages:        
<img width="692" height="366" alt="UBS-sudoAPT-update" src="https://github.com/user-attachments/assets/2417e8d8-f2fc-4c4e-a5b3-81f835c481d7" />

Then here is upgrading the system. It displays the packages that will be installed and would sometimes, exclude packages which maybe due to bugs.    
<img width="612" height="741" alt="UBS-sudoAPT-upgrade" src="https://github.com/user-attachments/assets/2fec549d-eb45-473a-8ef5-0cb1082de34f" />

# Using APT 
Next, let's talk about APT (Advanced Package Tool). APT is a command line tool used in Debian-based distos such Ubuntu and Debian to install, update, upgrade
and remove software. 

Since apt update and upgrade is shown earlier. Here is apt search, it searches for repositories from official Debian based on the keyword that is used. 
For example, searching for VLC:     
<img width="531" height="767" alt="UBS-apt-search" src="https://github.com/user-attachments/assets/91a0bd27-906e-48c8-93bf-2e0ffd0a73af" />

Now if I want to remove an installed software, I would use:
```md
sudo apt remove [software]
```
<img width="556" height="196" alt="UBS-sudoAPT-remove" src="https://github.com/user-attachments/assets/eb8d95e0-8bd6-4192-a624-146c02a6500f" />           


Sometimes, softwares that are removed may leave some residual files on the system. If I wanted to completely remove it, I would use:
```md
sudo apt purge [software]
```
<img width="562" height="211" alt="UBS-sudoAPT-purge" src="https://github.com/user-attachments/assets/147840cb-aec0-433b-aa89-cdd33f251ed8" />       

## Conclusion
In general, it is always a good practice to update software to keep our systems functioning properly and make more secure from ever emerging threats.
And for Debian-based systems like my homelab, the simplest way to do this is to use APT. 







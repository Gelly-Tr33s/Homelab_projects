## Configuring SSH

Now, I am going to configure SSH (secure shell). This is a network protocol that allows the server to be accessed remotely and securely. Before, there was Telnet. It is basically the same as SSH except
that it transmits credentials in plain text, making it very unsecure for today's standards. So SSH makes this access more secure by encrypting the credentials transmitted.

First, I installed the SSH on the server using
```md
sudo apt update && sudo apt install ssh
```
Here I can see the status of the ssh server (I haven't started this one)  

<img width="692" height="132" alt="UBS-ssh-installed" src="https://github.com/user-attachments/assets/49c2d0b8-c499-4719-bdf2-c23f7e1762a4" />

Next, I'll set it up.

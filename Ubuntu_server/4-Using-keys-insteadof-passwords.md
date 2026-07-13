# Using ssh keys
While using ssh is much more using than using Telnet, it can still be unsafe if we just use passwords. As passwords are prone to brute-force attacks.
So, I'll changing my authentication from using passwords to keys.

# Setup
This involves making a key on the client side. This means I have to make one on the client machine (Kali). This makes a private key (which stays on the vm) 
and a public key to be shared on the server.
This is done using the command
```md
ssh-keygen -t ed25519
```
The ed25519 is basically a secure digital signature algorithm best used in authentication such as ssh.

Afterwards it asks me for where to save and a passphrase. After doing all that, it provided me the key in which I won't show of course.
So when I checked the directory on where they are saved, they have the same name but different format. One without a .pub is the private key while the other one
with the .pub is the public key.

To copy the public key to the server, I use this commmand called
```md
ssh-copy-id -i [thePubFile] [server@IPofSERVER]
```

This ssh into the server and copy the public key in there. So if I went to the server itself, it should be there.   
<img width="227" height="47" alt="UBS-getting-pubkey" src="https://github.com/user-attachments/assets/0e21b241-509e-4064-af99-992f232f3b92" />

Now if I viewed that file the public key should be shown. When I checked it showed:
```md
sha-ed25519 [public_key] [usernameOfClientMachine]
```
which means I successfully copied the pub key to the server. With that done, I can configure ssh to use pubkeys instead of using passwords.

# Changing the configuration
So in the config file of ssh in server, these are commands that are modified:
```md
PasswordAuthentication no
PubkeyAuthentication yes
AuthorizedKeysFile [directory]
```
With all these configurations done, I restarted ssh.

# Adding private key in the client vm
In the client vm, the final step is to add the private key to the machine using
```md
ssh-add [privatekey]
```
I was asked for the passphrase and then it was added.

# Final result
This confirms that I have connected to my server remotely using ssh keys instead of passwords.    
<img width="557" height="172" alt="SSH-to-server-usingKeys-success" src="https://github.com/user-attachments/assets/5fba00a0-f971-4c68-b4b9-26562b3697d9" />

## Troubleshooting: SSH Public Key Authentication

### Problem

When I first tried SSH connections, it failed with:

Permission denied (publickey)

### The things I've investigated:

- Verified network connectivity
- Verified SSH service status
- Confirmed authorized_keys contents
- Verified file permissions
- Used `ssh -vvv` on the client
- Used `sshd -D -ddd` on the server

### When I try to check the config file again, I found the root cause:

The SSH configuration contained:

AuthorizedKeysFile ~/.ssh/authorized_keys

The tilde (`~`) is not expanded by sshd in this directive. This means that the ssh is finding the directory named "~". So I removed the "~" symbol.

### Solution

I changed the configuration to:

AuthorizedKeysFile .ssh/authorized_keys

Restarted the SSH service:

sudo systemctl restart ssh

Public key authentication then worked successfully.








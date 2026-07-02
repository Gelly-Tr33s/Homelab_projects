## Updating the Server

Before performing any configuration tasks, I updated the server to ensure that all package information and installed software were up to date.

First, I refreshed the package index:

```bash
sudo apt update
```

Then, I upgraded all installed packages to their latest available versions:

```bash
sudo apt upgrade
```

Keeping the system updated helps ensure security, stability, and compatibility before making further configuration changes.

## Creating Users, Configuring Sudo Permissions, and Creating Groups

I made 3 users in this server, named Alpha, Beta, and Charlie.  

<img width="472" height="632" alt="UBS-user-creations" src="https://github.com/user-attachments/assets/16ff3992-32dd-4488-8181-3c9c91de305b" />

Afterwards, I assigned user alpha to have administrator priviledges. Granting them full control of the server.  

<img width="382" height="81" alt="UBS-admin-priveledges" src="https://github.com/user-attachments/assets/055ec00b-fb24-4b82-a922-c3dacf0be8a3" />

Next, I made a group named "normalusers" which literally means they are normal users, no admin priviledges. Also, spelling is really important, otherwise the commandline returns nothing.

<img width="467" height="147" alt="UBS-groups-and-admin" src="https://github.com/user-attachments/assets/251cdac0-88db-481d-be02-1b8922821c79" />

In the real world, sharing a single account makes it impossible to track who actually changed what on the server. Using separate accounts fixes this and adds a major security layer: containment. 
If a regular user gets hacked or infected with malware, the damage is trapped. Because they don't have admin (root) privileges, the attacker can't touch sensitive system files, 
giving the admin time to kill the session and lock them out.

  
Now that these tasks are done. I'll be doing SSH (Secure Shell) configurations next.


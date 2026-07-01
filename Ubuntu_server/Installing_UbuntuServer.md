# Setting Up My Ubuntu Server Homelab

## Overview

The first step in my homelab project was installing **Ubuntu Server 26.04 LTS**. I downloaded the installation image from Ubuntu's official website and installed it on **Oracle VirtualBox**.

The purpose of this setup is to learn the fundamentals of Linux system administration, including installing and configuring a server, becoming comfortable with the Linux terminal, and building a foundation for more advanced homelab projects.

---

## Downloading Ubuntu Server

I downloaded the Ubuntu Server 26.04 LTS ISO from the official Ubuntu website.

**Official Download Page:**  
https://ubuntu.com/download/server

![Ubuntu Server Download Page](images/ubuntu-download-page.png)

---

## Creating the Virtual Machine

After downloading the ISO file, I created a new virtual machine in Oracle VirtualBox and attached the Ubuntu Server ISO as the installation media.

![Oracle VirtualBox Configuration](images/virtualbox-setup.png)
![Oracle VirtualBox Configuration2](images/virtualbox-setup2.png)

 
## Installing the Server
![Ubuntu Server Installation](images/ubuntu-server-start.png)
And here's what it looked like once it is installed:
![Ubuntu Server Installed](images/ubuntu-server-install-finished.png)

---

# Planned Configuration Tasks

After completing the Ubuntu Server installation, I will perform the following system administration tasks:

- [ ] Create multiple user accounts
- [ ] Create user groups
- [ ] Configure `sudo` permissions
- [ ] Configure SSH
- [ ] Disable SSH password authentication
- [ ] Update installed packages
- [ ] Install software using `apt`
- [ ] Schedule automatic security updates
- [ ] Configure the system hostname
- [ ] Configure the firewall using UFW

---

## Learning Goals

By completing these tasks, I aim to:

- Understand Linux user and group management.
- Learn basic system administration.
- Practice securing a Linux server.
- Become more comfortable using the command line.
- Build a strong foundation for future homelab projects involving networking, virtualization, and server management.
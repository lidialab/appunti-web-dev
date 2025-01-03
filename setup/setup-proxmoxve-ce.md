# Proxmox VE Community Edition setup

(first try)

Installing it from YUMI/Ventoy doesn't work, made a dedicated usbkey.

First steps after installation:

- added the second disk as the destination for VMs; wiped it; inizialized with GPT; created a directory with ext4 fs;
- added ISOs from USB key (manually mounted) to ```/var/lib/vz/template/iso```


First Linux server VM creation:

- "Create VM" from top-right button
- General: choosing a name
- OS: choosing a Linux ISO image; Type Linux; Version 6.x Kernel
- System: Qemu Agent checked
- Disks: Discard checked (trim per SSD); Size 42GB; vms directory choosen (2nd disk)
- CPU: 2 cores
- Memory: 4096 MiB
- Network: default
- Confirm


VMs cloning:

- change hostname
```sudo hostnamectl set-hostname nuono_nome```

- change host fingerprints
```cd /etc/ssh
sudo rm ssh_host_*
sudo dpkg-reconfigure openssh-server```


Post inst steps:

- ssh access
- sudo apt update && sudo apt dist-upgrade -y
- sudo apt install qemu-guest-agent
- systemctl status qemu-guest-agent.service
- sudo systemctl start qemu-guest-agent.service
- install sw you need
- lower VM's cpu and ram if not needed

VMs templates:

- sudo apt update && sudo apt dist-upgrade -y
- sudo apt install cloud-init
- sudo apt install qemu-guest-agent
- sudo apt clean
- sudo apt autoremove 
- (ubuntu)  sudo truncate -s 0 /etc/machine-id
- sudo rm /etc/ssh/ssh_host_*

After cloning a template:

- sudo dpkg-reconfigure openssh-server
- sudo hostnamectl set-hostname nuovo-nome-server
- sudo nano /etc/hosts (change 127.0.0.1 row in nuovo-nome-server)
- reboot


Error:
If you receive:

- "failed to connect to https //changelogs.ubuntu.com/meta-release-lts. Check your Internet Connection or Proxy Settings"

--> sudo apt reinstall ubuntu-release-upgrader-core

- 

--> 


Container:





ref: https://www.youtube.com/playlist?list=PLT98CRl2KxKHnlbYhtABg6cF50bYa8Ulo (lessons 1 to 6 + Win lesson)

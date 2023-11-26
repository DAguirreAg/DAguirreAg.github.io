---
title: 'Setting up my own Home lab: Software'
date: 2023-11-25T18:51:39+01:00
author: Daniel Aguirre
draft: false
tags: ["homelab", "raspberrypi", "software", "networking", "SSH", "docker", "Pi-Hole"]
cover:
  image: images/setting_up_my_own_home_lab_software/static_ip_address_tags.jpeg
---

With the homelab hardware set up, it is time to start preparing the machines so they can work together. As I intend to use my homelab as a safe and easy to use "IT playground", I have  decided that the following elements would need to be setup:
* Static IP address on each machine. This facilitates troubleshooting as well as easing the communication between the machines.
* Remote control software and SSH. This facilitates troubleshooting my "remote" machines without having to hook a keyboard+mouse+monitor to them.
* An Ads and Internet tracker blocking service. This should add extra network protection.
* Containerization software. This should facilitate the deployment of code as well as reduce issues with package dependencies.

## 1. Setting up static IP address (in Raspbian)
Setting up a static address in a Raspbian machine is quite straightforward. 
1. Get Raspberry Pi's IP address by typing: `hostname -I`.
2. Get my router's IP address by typing: `ip r`
3. Get Raspberry Pi's DNS IP address by typing: `nano /etc/resolv.conf`
4. Edit the following lines in the `dhcpcd.conf` file by typing: `nano /etc/dhcpcd.conf`:
    ```
    interface eth0
    static ip_address=192.168.0.132/24
    static routers=192.168.0.1
    static domain_name_servers=192.168.0.1
    ```
    (Note that your IP address values may be different)
5. Save changes by pressing `ctrl` + `x`.
6. Restart the machine.
7. (Optional) Add the static IP address tags to the machines.

{{<figure src="/images/setting_up_my_own_home_lab_software/static_ip_address_tags.jpeg" title="Static IP address tags." alt="Static IP address tags." width="100%">}}

## 2. Setting SSH and Remote control software
Follow next steps:
1. Click main menu.
2. Click `Preferences`.
3. Click `Raspberry Pi Configuration`.
4. Select the tab `Interfaces`.
5. Activate `SSH` and `VNC`.

(Note that in order to connect via VNC, I will have to install a VNC remote control software. In my case, I use `VNC viewer` due to its simplicity and availability in my Ubuntu OS).

{{<figure src="/images/setting_up_my_own_home_lab_software/enabling_ssh_and_vnc.png" title="Enabling SSH and VNC." alt="Enabling SSH and VNC." width="100%">}}

## 3. Installing Ads and Internet tracker blocking service (Pi-Hole)
Follow next steps:
1. Visit [https://docs.pi-hole.net/main/basic-install/](https://docs.pi-hole.net/main/basic-install/) and follow the instructions.
2. Visit [https://firebog.net/](https://firebog.net/) and note down the lists (urls) wanted to be added into Pi-Hole.
3. Visit Pi-Hole's address ([http://192.168.0.132/admin](http://192.168.0.132/admin) in my case).
4. Add noted down urls in the `Adlist` section.
5. Open a terminal window to add recently added lists to Pi-Hole by typing: `pihole -g`.
6. Go into your specific router's admin page and make sure to setup the Pi-Hole's IP address as your primary DNS. 

## 4. Installing Containerization software (Docker)
Follow next steps:
1. Update package manager index: `sudo apt update`
2. Upgrade packages: `sudo apt upgrade`
3. Download Docker "installer" script: `curl -fsSL https://get.docker.com -o get-docker.sh`
4. Execute Docker "installer" script: `sudo ./get-docker.sh`
5. (Optional) Add user to Docker usergorub to avoid having to type `sudo` everytime a command needs to be executed: `sudo usermod -aG docker [username]`



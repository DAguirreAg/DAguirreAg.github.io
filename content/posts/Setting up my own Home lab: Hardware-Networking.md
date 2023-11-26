---
title: 'Setting up my own Home lab: Hardware/Networking'
date: 2023-11-10T21:59:21+01:00
draft: false
tags: ["homelab", "raspberrypi", "networking"]
cover:
  image: images/setting_up_my_own_home_lab_hardware_networking/homelab_network_topology.png
---

As a data engineer, it is quite obvious that I like tinkering with technology, specially with software related stuff. Because of this, some time ago I decided to setup my own simple homelab where I could experiment and run scripts around without worrying about setting up cloud services.

As such, I have decided to share how I set up my homelab, so others can use it as an inspiration or just have a look at it.

## 1. Requirements
No project can start without the prior requirement gathering. Next I am displaying the main points I want to get in my homelab:
* Hardware-wise
  * Low power consumption (as I plan to have projects running 24/7).
  * Low noise (as I will place it near my living room).
  * Low cost setup.
* Software-wise
  * Monitor network activity.
  * Run projects 24/7.

## 2. Hardware
Based on the requirements and a little bit of research (and availability of the devices), I settled down for the following:
* Raspberry Pi 4 Model B (8Gb ram)
* Raspberry Pi 3 Model B +
* TP Link TL-WR940N (Router)
* Main Desktop PC
* Seagate Expansion Portable Hard Drive SRD0NF1 (external HDD)

{{<figure src="/images/setting_up_my_own_home_lab_hardware_networking/hardware.jpg" title="Homelab hardware." alt="Homelab hardware." width="100%">}}

## 3. Network architecture/topology
The devices communicate with each other via ethernet connection, all of them connected through a centralized router. Note that even though the router is a single Point-Of-Failure, it is very unlikely to happen, and none of the services I am running are critical enough to consider for a redundant solution. Find below the topology of my homelab:

{{<figure src="/images/setting_up_my_own_home_lab_hardware_networking/homelab_network_topology.png" title="Overview of Network topology." alt="Overview of Network topology." width="100%">}}

## Future steps
Ideally, I would like to have another Raspberry Pi 4 fully dedicated to experimentation. This should allow me to identify issues that may arise when deploying services in my 24/7 running Raspberry Pi 4, without risking breaking it. 

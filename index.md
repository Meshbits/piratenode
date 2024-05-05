---
layout: home
title: Host personal pirate chain full node from home # name of the site
---

## About this project

The purpose of this website is to be a placeholder for easy to access guides and tutorials for setting up a personal pirate chain full node at home.
The tutorials and guides on this website may not be perfect, but could give you some ideas and starting point to get started with how to achive it.

## Why this project exists

In true Bitcoin's nature, the author(s)/contributor(s) of this website beleives there must be resources made available for people to allow them to build and manage personal full node of Pirate Chain blockchain. Every day we witness another news hitting central point in cryptocurrency industry which gets hit by the centralised authorities, resulting in taken down of the services which played important role in cryptocurrency space. This project just tries to help build more peer nodes on the network which are controled and operated by regular users with low and minimal efforts possible, and in much efficient resources, resulting to help stronger decentralisation in Pirate Chain network.

## Table of contents

- [Buy Raspberry Pi kit](#buy-raspberry-pi-kit)
- [How to find the node on network and connect to it](#)
- [Upgrade OS, update SWAP size, configure WiFi, install packages git, htop](#)
- [Install Tor and setup onion node](#)
- [Install Pirate full node and configure it](#)
- [Make pirate system service to run automatically on system startup](#)
- [Install Golang](#)
- [Make TLS certificate for lightd](#)
- [Install lightwalletd and configure it](#)
- [Make lightd system service and startup on system boot](#)
- [Find and configure dynamic DNS service, ddnsc configuration to update IP on cloud flare, name cheap and others](#)
- [Test, setup and try how to setup DUCKDNS.](#)
- [How to use tmux for basic monitoring of log files and running process in background ](#)
- [Configuring Tor service on macOS and Linux to Abe able connect the pirate lightd over Tor network from anywhere](#)
- [How to find and connect with other pirate Tor node peers](#)


## Buy Raspberry Pi Kit

The most basic requirements to get started with a personal pirate node at home is to use Raspberry Pi.
And Raspberry Pi 5 is the best fit.

### Why Raspberry Pi

 - Small in size.
 - Extremely efficient on power.
 - Widely available Globaly in nearby computer hardware stores or easily purchasable through online shopping.
 - Has the biggest commmunity support for it's Operating System, software and any other 3rd party hardware add on if you ever wish to extend it's use your self.
 - Perfect for Do It Yourself (DIY) types of projects.
 - Uses Linux and Open Source standards in both software and hardware.

### Following are the MUST have hardware

 1. [Raspberry Pi 5 board](https://www.raspberrypi.com/products/raspberry-pi-5/)
 2. [Raspberry Pi Power Supply](https://www.raspberrypi.com/products/27w-power-supply/)
 3. [Raspberry Pi 5 Case](https://www.raspberrypi.com/products/raspberry-pi-5-case/)
 4. microSD Card - Recommended any 128GB or more storage microSD Memory Card. Samsung and SankDisk are the best known microSD cards for such project.
 5. USB SD Card Adapter - You just need the ability to attach the microSD Card to your computer to install Raspberry Pi Operating System on it. And there are many forms of SD Card adapters. Find USB-A or USB-C type adapters for this guide.

### MicroSD Card links

 - [Samsung Evo Plus 128 GB](https://www.amazon.com/SAMSUNG-Adaptor-Expanded-MB-MC128KA-AM/dp/B0B1VMJ394)
 - [SanDisk 128GB Extreme](https://www.amazon.com/SanDisk-Extreme-microSDXC-Memory-Adapter/dp/B09X7BK27V)

### USB SD Card Adapter

 - [uni SD Card Reader (Amazon's Choice)](https://www.amazon.com/uni-Adapter-Supports-Compatible-MacBook/dp/B081VHSB2V)

### Other Good Raspberry Pi 5 Cases

 1. [Argon NEO 5 M.2 NVME PCIE Case for Raspberry Pi 5](https://argon40.com/products/argon-neo-5-m-2-nvme-for-raspberry-pi-5) - [Video Link](https://www.youtube.com/watch?v=5Su4u4G-VIk)

 2. [Argon ONE V3 M.2 NVME PCIE Case](https://argon40.com/products/argon-one-v3-m-2-nvme-case) - [Video Link](https://www.youtube.com/watch?v=DQG21yJ-upk)


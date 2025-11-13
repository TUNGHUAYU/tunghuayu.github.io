---
layout: post
title: 'linux driver: Prepare environment by virtual machine'
categories:
- linux driver
tags:
- driver
- linux
- lima
date: 2025-11-14 01:07 +0800
---
Johannes has provided the serial tutorial for linux driver development. <br>
It mainly base on "raspberry Pi 3". However, I don't have that device so that I adopt the virtual machine way. <br>
You don't need the physical board and can demo those project just with notebook.

## Commands

```bash
# Create virtual machine (ubuntu-24.04)
$ limactl create --name ubuntu-24.04 --cpu 1 --memory 1 /opt/homebrew/share/lima/templates/ubuntu-24.04.yaml

# Run virtual machine and enter terminal TUI
$ limactl start ubuntu-24.04
$ limactl shell ubuntu-24.04

# Download "Linux Driver Tutorial" repository
$ cd ~
$ git clone https://github.com/Johannes4Linux/Linux_Driver_Tutorial.git
$ cd Linux_Driver_Tutorial/

# Install required packages
$ sudo apt install make
$ sudo apt install build-essential
```


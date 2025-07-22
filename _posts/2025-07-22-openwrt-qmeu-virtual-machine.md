---
layout: post
title: OpenWRT - qmeu virtual machine (DRAFT)
date: 2025-07-22 23:28 +0800
categories: [OpenWRT]
tags: [openwrt, qemu]     # TAG names should always be lowercase
---


# How-to build openwrt image

```bash
# download repository 
# update feeds 
# install feeds
# compile target
$ git clone https://github.com/openwrt/openwrt.git # commit 4ff02b46b9 @ 20250718 
$ cd openwrt/
$ ./script feed update -a 
$ ./script feed install -a
$ make menuconfig

# menu ###################
# target system -> ()

```

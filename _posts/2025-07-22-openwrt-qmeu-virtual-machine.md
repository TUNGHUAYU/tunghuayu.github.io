---
layout: post
title: OpenWRT - qmeu virtual machine
date: 2025-07-22 23:28 +0800
categories: [OpenWRT]
tags: [openwrt, qemu]     # TAG names should always be lowercase
---

- [Brief](#brief)
- [Build openwrt image (armsr)](#build-openwrt-image-armsr)
- [Run openwrt image on qemu](#run-openwrt-image-on-qemu)
  - [Command Line Interface](#command-line-interface)
  - [UTM GUI](#utm-gui)
- [Connect Host and virtual machine](#connect-host-and-virtual-machine)



## Brief

This topic shared about the way how generate an arm-based openwrt image. 
OpenWRT provides build-in TARGET (armsr) that genearte arm-based images.

## Build openwrt image (armsr)

```bash
# Download repository 
# commit 4ff02b46b9 @ 20250718 
$ git clone https://github.com/openwrt/openwrt.git 
$ cd openwrt/
$ ./script feed update -a 
$ ./script feed install -a
$ make menuconfig

# Configurate  
# Change Target System (Arm SystemReady (EFI) compliant)
# Check by ./script/diffconfig.sh
CONFIG_TARGET_armsr=y
CONFIG_TARGET_armsr_armv7=y
CONFIG_TARGET_armsr_armv7_DEVICE_generic=y

# compile
$ make
```

<br>

## Run openwrt image on qemu

### Command Line Interface

```bash

# Collect image and uboot
mkdir qemu-arm-virt-image/
cp openwrt/bin/targets/armsr/armv7/openwrt-armsr-armv7-generic-squashfs-combined-efi.img.gz .
cp openwrt/bin/targets/armsr/armv7/u-boot-qemu_armv7/u-boot.bin .

# Move to workspace folder
cd qemu-arm-virt-image/
gzip -d openwrt-armsr-armv7-generic-squashfs-combined-efi.img.gz

# Activate
qemu-system-arm \
  -M virt \
  -cpu cortex-a15 \
  -m 512M \
  -bios u-boot.bin \
  -drive if=none,file=openwrt-armsr-armv7-generic-squashfs-combined-efi.img,id=hd0,format=raw \
  -device virtio-blk-device,drive=hd0 \
  -netdev user,id=net0,hostfwd=tcp::2222-:22 \
  -device virtio-net-device,netdev=net0 \
  -nographic

qemu-system-arm \
  -M virt \
  -cpu cortex-a15 \
  -m 512M \
  -bios u-boot.bin \
  -drive if=none,file=openwrt-armsr-armv7-generic-ext4-combined-efi.img,id=hd0,format=raw \
  -device virtio-blk-device,drive=hd0 \
  -netdev user,id=net0,hostfwd=tcp::2222-:22 \
  -device virtio-net-device,netdev=net0 \
  -nographic

```

### UTM GUI

todo: UTM GUI approach



## Connect Host and virtual machine






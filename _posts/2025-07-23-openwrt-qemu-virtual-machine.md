---
layout: post
title: OpenWRT - qemu virtual machine
categories:
- OpenWRT
tags:
- openwrt
- qemu
date: 2025-07-23 00:00 +0000
---
- [Brief](#brief)
- [Build openwrt image (armsr)](#build-openwrt-image-armsr)
- [Run openwrt image on qemu](#run-openwrt-image-on-qemu)
  - [CLI (qemu-system-arm)](#cli-qemu-system-arm)
  - [GUI (UTM)](#gui-utm)
- [References](#references)



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

### CLI (qemu-system-arm)

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

### GUI (UTM)

todo: UTM GUI approach

Install UTM on macos via [utm official website][3]

Setup UTM virtual machine via [openwrt utm tutorial page][1]

``` bash
# check openwrt LAN configuration
root@openwrt:~# uci show network.lan

# change LAN ipaddress for SSH connection
root@openwrt:~#  uci set network.lan.ipaddr='10.0.2.2'
root@openwrt:~#  uci commit
root@openwrt:~#  service network restart
```

``` bash
user@mac $ ssh root@10.0.2.2
```

![image](/assets/img/post/utm-armvirt-openwrt-ssh.png)


## References

- [1][1] openwrt forum / Using utm (qemu GUI) to bring up openwrt image 
- [2][2] markuta       / Using qemu CLI to bring up openwrt image 
- [3][3] utm           / utm official website

[1]: https://openwrt.org/docs/guide-user/virtualization/utm
[2]: https://markuta.com/openwrt-qemu-m1/
[3]: https://mac.getutm.app

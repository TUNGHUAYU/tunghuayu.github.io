---
layout: post
title: OpenWRT - devtool - new hellowrold package (DRAFT)
date: 2025-07-24 19:41 +0800
categories:
- OpenWRT
tags:
- openwrt
- devtool
---



## Quick start

```bash
# Download openwrt
$ git clone <openwrt-url>
$ cd openwrt/
$ make

# Download openwrt_devtool
$ git clone https://github.com/TUNGHUAYU/openwrt_devtool.git
$ cd openwrt_devtool/

# New package from built-in sample ( hello-world )
# $ devtool new <pkg-name>
$ devtool new my-hello-world


search_path: /home/terryyu.linux/openwrt_devtool/.devtool/ref-Makefile/

---
|No.  |PKG-NAME                      |PKG-PATH                                           

|1    |Makefile.autotools.generic    |${search_path}/Makefile.autotools.generic          
|2    |Makefile.cmake.generic        |${search_path}/Makefile.cmake.generic              
|3    |Makefile.none.prpl_plugin     |${search_path}/Makefile.none.prpl_plugin           
---
Please select Makefile style:
Select: 2

Select: Makefile.cmake.generic

PKG_NAME:=my-hello-world
PKG_SOURCE_VERSION:=dev
PKG_SOURCE_URL:=file:///home/terryyu.linux/openwrt_devtool/workspace/SOURCES/my-hello-world
    CATEGORY:=devtool-pkg
    SUBMENU:=misc
    TITLE:=short description here
    long description here

search_path: /home/terryyu.linux/openwrt_devtool/.devtool/ref-sources/

---
|No.  |PKG-NAME                      |PKG-PATH                                           

|1    |cmake_hello-world             |${search_path}/cmake_hello-world                   
|2    |none_prpl-plugin-generic      |${search_path}/none_prpl-plugin-generic            
---
Please select sample source:
Select: 1

Select: cmake_hello-world

Initialized empty Git repository in /home/terryyu.linux/openwrt_devtool/workspace/SOURCES/my-hello-world/.git/
[master (root-commit) 323d8e0] first commit
 6 files changed, 80 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 CMakeLists.txt
 create mode 100644 README.md
 create mode 100644 inc/foo.h
 create mode 100644 src/foo.c
 create mode 100644 src/main.c
Switched to a new branch 'dev'
Activate feed -> "src-link feed_devtool"
Updating feed 'feed_devtool' from '/home/terryyu.linux/openwrt_devtool/workspace/FEEDS/feed_devtool' ...
Create index file './feeds/feed_devtool.index' 
Collecting package info: done
Installing package 'my-hello-world' from feed_devtool
```


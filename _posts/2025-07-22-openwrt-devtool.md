---
title: OpenWRT - devtool (DRAFT)
categories:
- OpenWRT
tags:
- openwrt
- devtool
date: 2025-07-22 23:48 +0800
---

- [Introduction](#introduction)
- [Layout](#layout)
- [Example](#example)

# Introduction

The devtool provides the following features:
1. **Modify** the package from openwrt codebase.
2. **New** the package to openwrt codebase by *built-in example* or *remote url repository*.
3. **List** all packages in devtool workspace.
4. **Abort** the package in devetool workspace.

The major idea is duplicate the target package to seperate workspace 

# Layout 

```bash
<user>/
├── openwrt/             # openwrt codebase
└── openwrt_devtool/     # openwrt devtool 
	├── devtool.sh*          # main progress
	├── history.md
	├── readme.md
	└── workspace/	         # workspace ( new/modify packages )
		├── FEEDS/
		└── SOURCES/
```

**todo**: complete layout tree diagram ( sub-folders below workspace/ )


# Example

There are serveral example below:
- Prepare openwrt image and run it on qemu. [link]({% link _posts/2025-07-22-openwrt-qmeu-virtual-machine.md%})
- Create new package, hello world package.  [link]({% link _posts/2025-07-24-openwrt-devtool-new-hellowrold-package.md%})
- Modify existed package. [todo]()



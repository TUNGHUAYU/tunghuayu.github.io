---
layout: post
title: linux driver Johannes4Linux lesson 1 - Hello World
categories:
- linux driver
tags:
- driver
- linux
- lima
date: 2025-11-15 20:00 +0800
---

Follow the post [1][1] to setup environment.



```bash
# Download repository "Linux Driver Tutorial"
$ cd ~
$ git clone https://github.com/Johannes4Linux/Linux_Driver_Tutorial.git
$ cd Linux_Driver_Tutorial/

# Compile hello module
$ cd 01_hello/
$ make

# install module
$ sudo insmod hello.ko

# remove module
$ sudo rmmod hello.ko
```

hello.c
```c
#include <linux/module.h>
#include <linux/init.h>

int my_init(void)
{
	printk("hello - Hello, Kernel!\n");
	return 0;
}

void my_exit(void)
{
	printk("hello - Goodbye, Kernel!\n");
}

module_init(my_init);
module_exit(my_exit);

MODULE_LICENSE("GPL");
```

---

The below video demo the hello.ko behavior.

<video width="640" controls>
  <source src="https://youtu.be/OXOvedbwlkE">
  Your browser doesn’t support HTML5 video.
</video>


---

[1]: {% post_url 2025-11-14-practice-linux-driver-by-virtual-machine-in-macos %}
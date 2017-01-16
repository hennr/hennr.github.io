---
layout: post
title:  "Get more space on usb sticks"
categories: linux
---

I almost forgot that most file systems under Linux (e.g. ext4) are mostly set to reserve 5% of every created file system for privileged users.
While this is useful on your root file system if your HD is full but you still want to be able to login as root it’s not too useful on usb sticks / pure storage devices.

Anyway I want more space on my usb stick, let’s see what we can do on my stick:

Here we see the default reservation of 5%:

    # df -h /dev/sdd1
    Filesystem Size Used Avail Use% Mounted on
    /dev/sdd1   29G  11G   17G  40% /foo

Now we change that value to 0%:

    # tune2fs -m 0 /dev/sdd1
    tune2fs 1.42-WIP (02-Jul-2011)
    Setting reserved blocks percentage to 0% (0 blocks)

Et voilà, 1GB more space to waste:

    # df -h /dev/sdd1
    Filesystem Size Used Avail Use% Mounted on
    /dev/sdd1   29G  11G   18G  38% /foo

Please note that these 5% reservation is also used to avoid fragmentation of the partition (see man tune2fs).

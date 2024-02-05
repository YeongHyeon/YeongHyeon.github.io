---
layout: post
categories: posts
title: Automounting external drive in Ubuntu
tags: [Setting]
date-string: MAY 29, 2019
---

This post covers how to automount the external drive.

### 1. Listing all connected drives  
``` sh
$ lsblk

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sdb      8:16   0   2.7T  0 disk
sdc      8:32   0   477G  0 disk
├─sdc2   8:34   0     1M  0 part
├─sdc3   8:35   0  63.9G  0 part [SWAP]
├─sdc1   8:33   0   512M  0 part /boot/efi
└─sdc4   8:36   0 412.5G  0 part /
sda      8:0    0   1.8T  0 disk
└─sda1   8:1    0   1.8T  0 part
```

### 2. Confirming UUID for each drive  
``` sh
$ ls -l /dev/disk/by-uuid

lrwxrwxrwx 1 root root 10  5월 29 18:13 0066a5ea-5a20-4f2c-818b-560e49f04637 -> ../../sdc3
lrwxrwxrwx 1 root root 10  5월 29 18:13 411c907b-9770-4c4f-9f76-ce536e0634dd -> ../../sda1
lrwxrwxrwx 1 root root  9  5월 29 18:13 67fa5f60-0664-4b99-b2e8-fa2ca07e4d39 -> ../../sdb
lrwxrwxrwx 1 root root 10  5월 29 18:13 8b76ca2c-6d1e-4606-880d-7a298eea7535 -> ../../sdc2
lrwxrwxrwx 1 root root 10  5월 29 18:13 E7D4-2463 -> ../../sdc1
lrwxrwxrwx 1 root root 10  5월 29 18:13 d8ac0ce3-9c7f-4a5e-a60c-528dbf1b541f -> ../../sdc4
```

### 3. Registration UUID to <a href="https://en.wikipedia.org/wiki/Fstab">fstab</a>  
``` sh
$ sudo vi /etc/fstab
```
Before registration, you can see as following.
``` sh
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda4 during installation
UUID=d8ac0ce3-9c7f-4a5e-a60c-528dbf1b541f /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=E7D4-2463  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=0066a5ea-5a20-4f2c-818b-560e49f04637 none            swap    sw              0       0
```
Then, add unmounted drives as following.
``` sh
# 1.8T HDD
UUID=411c907b-9770-4c4f-9f76-ce536e0634dd /home/{username}/hdisk01  ext4  defaults  1 2

# 2.7T HDD
UUID=67fa5f60-0664-4b99-b2e8-fa2ca07e4d39 /home/{username}/hdisk02  ext4  defaults  1 2
```

### 4. Rebooting and confirmation
``` sh
$ df -h

Filesystem      Size  Used Avail Use% Mounted on
udev             32G     0   32G   0% /dev
tmpfs           6.3G  9.6M  6.3G   1% /run
/dev/sdc4       406G  7.4G  378G   2% /
tmpfs            32G  196K   32G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs            32G     0   32G   0% /sys/fs/cgroup
/dev/sdb        2.7T   32G  2.6T   2% /home/yeonghyeon/hdisk02
/dev/sdc1       511M  3.7M  508M   1% /boot/efi
/dev/sda1       1.8T  259G  1.5T  15% /home/yeonghyeon/hdisk01
tmpfs           6.3G  8.0K  6.3G   1% /run/user/1000
tmpfs           6.3G   32K  6.3G   1% /run/user/108

```

---
layout: post
categories: posts
title: Remote Desktop Protocol Setup for Ubuntu
tags: [Setting]
date-string: AUGUST 19, 2019
---

This post covers how to set up the remote desktop protocol for connecting Ubuntu. This method does not need a physical monitor for using GUI. VNC viewer can be basically used for connection but it needs physical monitor attachment.

### 1. Install 'XRDP' and 'Xfce Desktop Environment'
``` sh
sudo apt-get update   
sudo apt-get install xrdp

sudo apt-get install xfce4
```

### 2. Add Xfce session to '.xsession' and initialize 'XDRP'
``` sh
echo xfce4-session > ~/.xsession
sudo service xrdp restart
```

### 3. Connect remote PC via remote desktop application

<a href="https://apps.apple.com/us/app/microsoft-remote-desktop-10/id1295203466?mt=12">Microsoft Remote Desktop App</a>

The GUI may look different from the original Ubuntu GUI (but work samely).

<center>
    <div>
        <img src="/images/2019-08-19/rdp.png">
    </div>
</center>


### Troubleshooting

#### Empty screen

When you get the black or blue screen without any icon (in Desktop), enter the following commands.

``` sh
sudo apt-get remove xorgxrdp
sudo apt-get install xorgxrdp

sudo service xrdp restart
```

#### Access at other network

First, open the 'xdrp.ini'.

``` sh
sudo vi /etc/xrdp/xrdp.ini
```

Port number is originally '3389'.
You need to change it to other number for example 1234.
Then, restart xrdp and Desktop.

``` sh
sudo service xrdp restart
sudo reboot
```

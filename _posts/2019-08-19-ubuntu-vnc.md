---
layout: post
categories: posts
title: VNC Setup for Ubuntu
tags: [Setting]
date-string: AUGUST 19, 2019
---

This post covers how to set up the desktop sharing for connecting Ubuntu via VNC. This method needs a physical monitor for using GUI.

### 1. Go to sharing menu
<center>
    <div>
        <img src="/images/2019-08-19/figure1.png">
    </div>
</center>

### 2. Screen sharing setting

<center>
    <div>
        <img src="/images/2019-08-19/figure2.png">
    </div>
</center>

Toggle the off state to on state.
Then, set the password.

<center>
    <div>
        <img src="/images/2019-08-19/figure3.png">
    </div>
</center>


### 3. Install 'dconf-editor'

``` sh
sudo apt-get install dconf-editor

dconf-editor # run the dconf-editor
```

<center>
    <div>
        <img src="/images/2019-08-19/figure4.png">
    </div>
</center>

Turn off the require-encryption.

<center>
    <div>
        <img src="/images/2019-08-19/figure5.png">
    </div>
</center>

### 4. Connecting in Windows

Download <a href]"https://www.realvnc.com/en/connect/download/viewer/">'VNC viewer'</a> or use installed another program (such as command+K in macOS).
Then connect via IP.

<center>
    <div>
        <img src="/images/2019-08-19/figure6.png">
    </div>
</center>

### 5. Use it

Finally, you can use Ubuntu via VNC viewer with GUI.

<center>
    <div>
        <img src="/images/2019-08-19/figure7.png">
    </div>
</center>

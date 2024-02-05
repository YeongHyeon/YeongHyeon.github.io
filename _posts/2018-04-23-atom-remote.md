---
layout: post
categories: posts
title: Source code management with atom and remote-ftp package.
tags: [Setting]
date-string: APRIL 23, 2018
---

### 1. Install atom and remote-ftp package

Before managing source code, install the <a href="https://atom.io/">atom</a> editor. Then, download <a href="https://atom.io/packages/remote-ftp">remote-ftp</a> package in the atom editor.  

After download atom and remote-ftp package, turn on the remote-ftp package by following sequence.
<p>Top menu > Package > Remote FTP > Toggle</p>
Following figure will be presented after above procedure.

<center>
    <div>
        <img src="/images/2018-04-23/package.png">
        <p>Remote-ftp window in atom</p>
    </div>
</center>

### 2. Setting for connecting

First, press the 'edit configuration' button. You can meet new page for typing your configuration. Just type the configuration as following example.

```
{
    "protocol": "sftp",
    "host": "{123.456.789.001}", // IP or something
    "port": 22,
    "user": "{user name}",
    "pass": "{password}",
    "promptForPass": false,
    "remote": "{remote point for managing}", // recommending /home/user
    "secure": false,
    "secureOptions": null,
    "connTimeout": 10000,
    "pasvTimeout": 10000,
    "keepalive": 10000,
    "watch": []
}
```

I recommend you to refer <a href="https://atom.io/packages/remote-ftp">https://atom.io/packages/remote-ftp</a> for adjusting other detail properties. After typing above contents, save them with name as '.ftpconfig'.

### 3. Connect to remote computer

Finally, you can connect into remote computer by pressing 'connect' button.

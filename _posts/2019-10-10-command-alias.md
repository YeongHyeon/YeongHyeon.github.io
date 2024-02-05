---
layout: post
categories: posts
title: Alias Command in Linux (Unix)
tags: [Setting]
date-string: OCTOBER 10, 2019
---

Add alias command to '.bash_profile'.
``` sh
echo alias l='ls' >> ~/.bash_profile
echo alias alias ll='ls -al' >> ~/.bash_profile
```

Confirm '.bash_profile' using ```cat ~/.bash_profile```command.
``` console
alias l='ls'
alias ll='ls -al'
```

Activate edited '.bash_profile'.
``` sh
source ~/.bash_profile
```

Now, you can use alias commands in terminal!

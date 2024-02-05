---
layout: post
categories: posts
title: Install python with specific version on macOS
tags: [Setting]
date-string: DECEMBER 30, 2020
---

### Commands

``` sh
brew install python
brew install python@3.7
brew unlink python@{temporary version} && brew link python@{target version}
echo 'export PATH="/usr/local/opt/python@3.7/bin:$PATH"' >> /Users/{username}/.bash_profile
```

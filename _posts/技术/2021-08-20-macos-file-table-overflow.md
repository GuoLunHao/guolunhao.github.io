---
layout: single
title: "macos 中遇到 file table overflow 的解决方案"
date: 2021-08-20 11:07:00 +0800
tags: macOS
categories: 技术
---

最近在macOS 中频繁遇到 file table overflow 或 too many open file 的错误，导致chrome崩溃、nodejs无法运行。通过调大苹果系统的限制，来尝试解决该问题，目前体验良好，再观察一段时间。

```bash
echo kern.maxfiles=65536 | sudo tee -a /etc/sysctl.conf
echo kern.maxfilesperproc=65536 | sudo tee -a /etc/sysctl.conf
sudo sysctl -w kern.maxfiles=65536
sudo sysctl -w kern.maxfilesperproc=65536
ulimit -n 65536
```

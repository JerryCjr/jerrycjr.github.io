---
title: Connect VPN(L2TP) ERROR
date: 2020-02-26 21:09:36
tags:
  - VPN
  - L2TP
categories: Mac
---

# Mac 环境下连接 VPN 问题记录

## 错误信息如图

![nowrap](/images/mac/l2tp/mac_l2tp_error02.png)

## 系统信息如下

![nowrap](/images/mac/l2tp/mac_l2tp_error01.png)

## 解决方案

```bash
  cd ~/etc/ppp
  rm -rf ./options
```

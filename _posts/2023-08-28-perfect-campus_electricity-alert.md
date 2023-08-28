---
layout: post
title: 我写了一个脚本来提醒我充电费
categories: [Github]
description: 一个可以避免你忘记充电费的脚本
keywords: 完美校园, 脚本, shell
mermaid: false
sequence: false
flow: false
mathjax: false
mindmap: false
mindmap2: false
---

# 完美校园 低电费提醒🔔 [![完美校园低电费提醒](https://github.com/zuwei522/perfect-campus_electricity-alert/actions/workflows/main.yml/badge.svg?branch=main)](https://github.com/zuwei522/perfect-campus_electricity-alert/actions/workflows/main.yml)

你是否曾经因为忘记检查电费，而遭遇晚上断电，还恰好处于充值系统的维护时间？ /(ㄒoㄒ)/~~  
于是，为了避免悲剧再次发生，这个**使用 Github Action** 定时执行、借助 [Qmsg 酱](https://qmsg.zendee.cn/)发送低电费提醒的 **shell 脚本**就诞生了！ （好耶ヽ(✿ﾟ▽ﾟ)ノ

## 工作原理

- 本脚本默认在每天 12 点和 19 点，自动查询在完美校园上所绑定的所有房间或空调的剩余度数，若低于设定的阈值，就通过 Qmsg 酱向指定 QQ 推送消息。

## 开始使用

> 请移步至 Github 仓库查看👉 <https://github.com/zuwei522/perfect-campus_electricity-alert>

## 如果觉得不错，可以点个⭐Star 吗？

![求求你了](https://cdn.jsdelivr.net/gh/zuwei522/perfect-campus_electricity-alert/images/求求你了.jpg)

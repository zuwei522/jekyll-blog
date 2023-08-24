---
layout: post
title: 如何在 VS Code 中编译 C 程序
categories: [C, Visual Studio Code]
description: 配置 C 的编译环境和 VS Code
keywords: Visual Studio Code, VS Code, C
mermaid: false
sequence: false
flow: false
mathjax: false
mindmap: false
mindmap2: false
---

由于 VS Code 自身是不能直接编译 C 程序的，所以我们要为系统配置编译环境，然后再在 VS Code 中进行相关设置。

### 安装 VS Code 扩展包 [C/C++ Extension Pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools-extension-pack)

- 安装此扩展包会自动安装以下扩展：
  - C/C++
  - C/C++ Themes
  - CMake
  - CMake Tools

### 配置 C/C++ 环境

> 该步骤需安装 C++ 编译器，不同系统安装步骤有所不同。

#### 在 Linux 上安装 C++ 编译器

- 如果要为 Linux 进行 C++ 开发，建议安装 GCC 编译器。安装 GCC 十分简单，只需执行以下三个步骤:

    1. 从终端窗口运行以下命令以更新 Ubuntu 包列表。过期的 Linux 分发有时会干扰尝试安装新包。

            sudo apt update

    2. 使用此命令安装 GNU 编译器工具和 GDB 调试器:

            sudo apt install build-essential gdb

        由于 build-essential 是 Debian 系的 meta package 的名字，所以CentOS还需使用以下命令安装：

            yum install make automake gcc gcc-c++ kernel-devel

        或者安装大而全的包：

            yum groupinstall "Development Tools" "Development Libraries"

    3. 运行以下命令以验证 GCC 已安装。你应该会看到一条版权消息和有关所使用的 GCC 版本的信息。

            gcc --version

---
layout: post
title: Ext4 文件系统格式化后可用空间缩小怎么办？
categories: [Linux]
description: Ext4 文件系统格式化后可用空间缩小怎么办？
keywords: Ext4, Linux, 文件系统, 格式化
mermaid: false
sequence: false
flow: false
mathjax: false
mindmap: false
mindmap2: false
---

![文章封面][1]
最近在折腾玩客云，将原本NTFS文件系统的1T机械硬盘挂载上去，使用时 `ntfs-3g` 经常占用较大的 CPU 资源，导致读取缓慢、卡顿。于是将硬盘文件备份，重新创建 Ext4 格式的分区。但格式化之后，发现可用空间有较大“缩水”。💦


<!--more-->


## 预留空间
网上搜索了一番，发现原因之一是使用 `mkfs.ext4` 格式化分区时，默认会预留 5% 的空间。

> 为什么要预留空间呢？🤔
> - 留给root用户维护系统或者记录系统关键日志的时候使用

因为我不是用来做系统盘，所以没有必要，毕竟 1T 的盘可是要损失近 50G 的空间。￣へ￣

## inode 数量设置过大
> 在 Linux 的文件系统中，一个文件对应一个 inode。一个 inode 大小现在默认值是 256 字节。一个文件至少占用一个 inode，而 inode 数量是由格式化程序（这里就是 mkfs.ext4）根据自动算出来的。默认是 16K 一个 inode也就是说，就算你在这个分区全是 16K 小的文件，都有足够数量的 inode 使用。

也就是说，如果不是用来存储大量小文件的，完全可以减小 inode 的数量。比如我就是用来存视频、图片等大文件的，就可以适当减小 inode 数量。

## 解决方法
我这里使用 `mkfs.ext4` 来格式化，`-m` 参数设置预留空间百分比（0~100），`-i` 设置每多少字节分配一个 inode（我设置了1M，也就是 1048576 字节）。
```shell
mkfs.ext4 -m 0 -i 1048576 /dev/sda
```

## 参考文章
- [充分利用磁盘空间，打开ext文件系统的保留区块](https://luy.li/2010/01/08/reserved_block)
- [优化 Ext4 分区格式化后占用空间(通过降低inode数来节省磁盘空间)](https://blog.csdn.net/hunanchenxingyu/article/details/41832639)


  [1]: https://devconnected.com/wp-content/uploads/2021/03/lsblk-command.png

---
layout: wiki
title: Git 使用方法
cate1: 工具
cate2: 版本控制
description: Git 常用命令及使用方法
keywords: Git
type:
link:
mermaid: false
sequence: false
flow: false
mathjax: false
mindmap: false
mindmap2: false
---

# Git

## Git常用命令

| 命令名称                             | 作用           |
| :----------------------------------- | :------------- |
| git config --global user.name 用户名 | 设置用户签名   |
| git config --global user.name 邮箱   | 设置用户签名   |
| git init                             | 初始化本地库   |
| git status                           | 查看本地库状态 |
| git add 文件名                       | 添加到暂存区   |
| git commit -m "日志信息" 文件名      | 提交到本地库   |
| git reflog                           | 查看历史记录   |
| git reset --hard 版本号              | 版本穿梭       |

### 关于用户签名

- 签名的作用是区分不同操作者身份。用户的签名信息在每一个版本的提交信息中能够看
  到，以此确认本次提交是谁做的。 **Git 首次安装必须设置一下用户签名，否则无法提交代码。**
- **※注意：** 这里设置用户签名和将来登录 GitHub（或其他代码托管中心）的账号没有任
  何关系
- 在Windows下，设置的用户签名保存在用户文件夹下的`.gitconfig`文件中。

### 关于移除暂存区中的文件

- `git rm --cached 文件名`

### 关于切换回指定历史版本

- `git reset --hard 版本号`

## Git分支命令

| 命令名称            | 作用                         |
| ------------------- | ---------------------------- |
| git branch 分支名   | 创建分支                     |
| git branch -v       | 查看分支                     |
| git checkout 分支名 | 切换分支                     |
| git merge 分支名    | 把指定的分支合并到当前分支上 |

### 关于查看分支命令

```bash
$ git branch -v
* master 087a1a7 my third commit
```

- `*`表示当前所在分支

### 关于合并分支

- 示例：在“分支1”下使用命令`git merge 分支2`，即为将“分支2”合并至“分支1”。
- 若遇合并冲突，则需手动合并冲突文件。手动合并完成后添加至暂存区，在提交时只需`git commit -m "日志信息"`即可，无需在后面添加文件名。

## Git远程仓库命令

| 命令名称   | 作用 |
| ---------- | ---- |
| git remote |      |
|            |      |
|            |      |
|            |      |
|            |      |

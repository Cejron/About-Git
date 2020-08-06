# Git

### 目录

[背景](#)

[安装](#1.安装)

[配置](#2.配置)

[建库](#3.建库)

- [从本地分支到远程分支建库](#)

- [](#)

---
### 1.安装

下载Git并安装 [https://git-scm.com/download/win](https://git-scm.com/download/win)

---
### 2.配置

> 打开Git Bash，先自报下家门
```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

> 配置下ssh钥匙，用于ssh方式

1.git输入命令```ssh-keygen -t rsa -C "yourEmail"```需要按3次回车。
第1次是确认```id_rsa```和```id_rsa.pub```这两个文件生成的绝对路径，第2、第3次是用来设置push新的commit时需要输入的密码和确认密码，直接回车即默认无密码，这样以后push就不用密码

2.查看本地路径 c:\user\username\.ssh的 .ssh文件 下有无```id_rsa```和```id_rsa.pub```

3.复制```id_rsa.pub```内容至粘贴板

4.进入```github->setting->SSH and GPG keys->SSh keys->New SSH key```粘贴并保存

---
### 3.建库

1.文件夹+Git Bash Here 打开控制台

2.`ls -a`查看当前文件目录

3.`git init`初始化一个空的git仓库(文件目录下会多一个隐藏的.git文件)

4.`git status`查看文件状态(有没有被追踪)

  四种状态

  > Untracked 未被追踪
  
  > Modified 修改过但未add和commit
  
  > Staged add但未提交
  
  > Committed 已提交
  
  git三层结构

  > 工作区
  
  > 暂存区
  
  > 版本库
  
5.配置用户信息
  
  `git config --list`   查看配置
  
6.`git log` 查看提交信息

7.`git add .` 把所有文件从工作区添加到暂存区

8.`git commit -m'提交信息说明'` 将在暂存区的所有文件从暂存区提交到版本库

  直接使用 `git commit -am'提交信息说明'` 将所有在工作区的文件从工作区提交到版本库
  
-`git commit --amend` 取消上一次提交，并将暂存区重新提交到版本库

-`git checkout --filename` 撤销filename文件上次修改

  `git checkout -- .` 撤销所有文件上次修改
  
-`git reset HEAD filename` 将添加到暂存区的文件撤销回来

  `git reset 版本号 filename`
  
  
  

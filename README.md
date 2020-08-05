# Git

###目录

**安装**

**配置**

#### 1.下载Git [https://git-scm.com/download/win](https://git-scm.com/download/win)
 
#### 2.配置

打开Git Bash,自报下家门

```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"

```

配置下ssh钥匙,如果习惯使用HTTPS这种建库方式可能不会用到，但配一下总是好的。
就像考了驾照,虽然平时不开车用不到,但开车的时候就不用再考驾照。

```
ssh-keygen -t rsa -C "yourEmail"

查看本地路径c:\user\username\.ssh 的.ssh 文件下有无 id_rsa 和 id_rsa.pub

进入 github->setting->SSH and GPG keys->SSh keys->New SSH key

复制id_rsa.pub内容到New SSH key中

```
 
#### 3.从本地创建仓库到把本地代码上传到版本库

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
  
  `gitconfig--global user.name ***`
  
  `gitconfig--global user.email ***`
  
6.`git log` 查看提交信息

7.`git add .` 把所有文件从工作区添加到暂存区

8.`git commit -m'提交信息说明'` 将在暂存区的所有文件从暂存区提交到版本库

  直接使用 `git commit -am'提交信息说明'` 将所有在工作区的文件从工作区提交到版本库
  
9.`git commit --amend` 取消上一次提交，并将暂存区重新提交到版本库

10.`git checkout --filename` 撤销filename文件上次修改

  `git checkout -- .` 撤销所有文件上次修改
  
11.`git reset HEAD filename` 将添加到暂存区的文件撤销回来

  `git reset 版本号 filename`
  
  
  

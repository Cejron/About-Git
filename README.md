# Git

### 目录

[安装](#1.安装)

[配置](#2.配置)

[建库](#3.建库)
- [从本地分支到远程分支](#从本地分支到远程分支)
- [从远程分支到本地仓库](#从远程分支到本地仓库)

[其他](#4.其他)
- [常用命令](#常用命令)
- [ssh和https的区别](#sshhttps)
- [Master origin origin/Master区分](#masterorigin)
---
### 1.安装

下载Git并安装 [https://git-scm.com/download/win](https://git-scm.com/download/win)

---
### 2.配置

> 打开Git Bash，先自报下家门

```$ git config --global user.name "Your Name"```

```$ git config --global user.email "email@example.com"```

`git config --list`   查看配置，确认是否准确无误

> 配置下ssh钥匙，用于ssh方式

1.git输入命令```ssh-keygen -t rsa -C "yourEmail"```需要按3次回车。

第1次是确认```id_rsa```和```id_rsa.pub```这两个文件生成的绝对路径。

第2、第3次是用来设置push新的commit时需要输入的密码和确认密码，直接回车即默认无密码，这样以后push就不用密码

2.查看本地路径 c:\user\username\.ssh的 .ssh文件 下有无```id_rsa```和```id_rsa.pub```

3.复制```id_rsa.pub```内容至粘贴板

4.进入```github->setting->SSH and GPG keys->SSh keys->New SSH key```粘贴并保存

---
### 3.建库
##### 从本地分支到远程分支
`Initialize this repository without a README`
(倾向于把本地已有仓库push到github的版本库)

1.github上新建一个版本库，建库时不选`Initialize this repository with a README`

2.本地也建一个同名版本库+Git Bash Here

3.`echo "# description" >> README.md`---创建`README`

4.`git init`---本地仓库初始化(文件目录下会多一个隐藏的`.git`文件)

5.`git add README.md`---将`README.md`从工作区添加到暂存区，

也可以使用`git add .`将所有文件添加到暂存区。

6.`git commit -m'提交信息说明'` 将在暂存区的所有文件从暂存区提交到版本库。

直接使用 `git commit -am'提交信息说明'` 会将所有在工作区的文件从工作区提交到版本库。

`git log` 查看提交信息，不想看可以不看。
`git status` 查看文件状态(有没有被追踪)，同样不想看可以不看。

git的三层结构

> 工作区
  
> 暂存区
  
> 版本库

文件四种状态

> Untracked 未被追踪
  
> Modified 修改过但未add和commit
  
> Staged add 但未提交
  
> Committed 已提交

7.远程连接github的版本库，ssh方式和https方式有所不同。

ssh: `git remote add origin git@github.com:Cejron/learn.git`

https: `git remote add origin https://github.com/Cejron/learn.git`

8.`git push -u origin master`---第一次同步到远程。
后面只需要`git push`即可。

9.刷新github上的代码仓库。

##### 从远程分支到本地仓库
`Initialize this repository with a README`
(倾向于把github版本库拉取到本地仓库)

1.github新建版本库，建库时选择`Initialize this repository with a README`
建不建库无所谓，拿github上的其他已有版本库也可以。

2.本地新建同名的版本库+Git Bash Here

3.`git init`---初始化仓库。

4.`ssh方式:` `git remote add origin git@github.com:Cejron/learn.git`

或者`https方式:` `git remote add origin http://github.com/Cejron/learn.git` (仓库名.git)

远程连接github的版本库。

5.`git pull --rebase origin master` 将github的仓库拉到本地,远程将覆盖本地，至此github的分支就拉下来了。

6.然后可以各种`git add`和`git commit`,不喜欢可以不操作。

7.`git push -u origin master` 第一次同步到远程(github),这一步是为了之后可以直接`git push`、`git push`、`git push`。

这里要提一下，要是没有提交任何更新就执行该命令会报错`Everything up-to-date`

---
### 4.其他

#### 常用命令

创建和显示

`mkdir <flodername>`  创建名为<flodername>的文件夹

`pwd` 全称print working directory ，显示（打印）当前工作目录的绝对路径


删除，删除目录需要回到上层才能删

`rmdir <flodername>`  rmdir全称remove directory 移除空目录，只允许移除空目录，否则报错

`rm  -r  <dir>`递归删除  有子目录会提示是否删除目录和目录中的文件

`rm  -f  <dir>`强制删除不提示

`rm  -rf <dir1> <dir2> <dir3>`强制删除目录和目录下的文件不提示 后面可加多个目录名，用空格隔开


查找
`find . -type d -name <flodername> -exec rm -rf {}+`在当前目录下搜索名为<flodername>的目录
`. `当前目录下
`-type d` 只是搜索目录(可以理解为类型时dir)
`-name` 指定目录名
`-exec  rm -rf` 执行rm命令删除目录和目录下内容
`{}+` 在rm命令末尾追加

`ls-a` 查看当前目录文件(隐藏也看得到)

`git commit --amend` 取消上一次提交，并将暂存区重新提交到版本库

`git checkout --filename` 撤销filename文件上次修改

`git checkout -- .` 撤销所有文件上次修改
  
`git reset HEAD filename` 将添加到暂存区的文件撤销回来

`git reset 版本号 filename` 回滚某个文件到指定版本号

#### <span id="sshhttps">ssh和https的使用和区别</span>

参考  [git中使用https和ssh协议的区别以及它们的用法](https://www.cnblogs.com/wannananana/p/12059806.html)
  
#### <span id="masterorigin">Master origin origin/Master区分</span> 

`origin` 可以看作是github服务器，名为 `origin`

`Master` 本地分支，可以看作是远程分支的副本。

`origin/Master` 在远程服务器上的主要分支。

`Master`和`origin/Master`是各自的分支。

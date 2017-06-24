# github 

## github 简介
GitHub 是一个面向开源及私有软件项目的托管平台，因为只支持 Git 作为唯一的版本库格式进行托管，故名 GitHub。作为开源代码库以及版本控制系统，
Github拥有超过900万开发者用户。随着越来越多的应用程序转移到了云上，Github已经成为了管理软件开发以及发现已有代码的首选方法。在GitHub，
用户可以十分轻易地找到海量的开源代码。
## github 注册
注册比较简单，填写用户名，邮箱以及用户密码，只需要验证邮箱即可，邮箱的设置最好是国际邮箱。
## github 使用
### 创建仓库
可以在github上创建仓库，也可以创建文件夹，创建文件夹的时候写上文件夹名字然后加“/”就是创建了一个目录。删除目录直接删除即可。
在仓库中创建文件	在目录下可以创建文件，即markdown文档。形式如xxxx.md                     
Description (optional)：对仓库的描述介绍
PUBLIC：所有人都可看到
PRIVATE:外人不可看到，此业务需要付费
### 设置自身信息
### 克隆相关文件

## Linux仓库命令

### 转化为仓库
命令：git init <文件名>    把文件转化为一个仓库，在文件夹下拥有一个隐藏文件.git，表示创建仓库成功
### 仓库状态
* untracked: 文件未被加入的版本库中.
需要执行命令git add 文件名，把文件添加到版本库
* 执行命令git add .  把所有未被加入版本库的文件加入其中并进入
unmodified: 文件未被修改过.
此时文件不需要做什么操作
* modified: 文件已经被修改过了.
文件处于修改后状态，需要重新添加，提交，如果之前添加过可以利用直接使用命令
Commit –a即可提交，如果文件从未添加到版本库则需要先添加在提交 。
* staged: 准备好, 可以提交到版本库中了.
* git status :执行该命令可以查看当前仓库状态
* git log :查看当前提交的版本
* git config –globle user.email “邮箱”
* git config –global user.name “名字”

### 版本回退

定义：什么叫版本, 一次提交就相当于一个版本. 如果更准确的说是提交的回退. 每一次提交都会将修改的状态提交到仓库中保存着, 这些信息都保存那里呢?都保存在.git的目录下.                                      
操作：如果想回退到上次提交的版本, 那么需要使用git reset命令
git reset --hard commitID  （commitID是提交成功后的版本号）可以用git vim 文件名查看是否回到相关版本。
这时查看提交状态执行git relog即可

### 仓库删除文件

定义：如果将文件从仓库中删除这个文件, 需要使用git rm
操作：git rm filename
这只是做了删除操作, 但没有真正的从仓库中删除, 我们只要将删除再做一次提交到仓库.
git commit
这时就真正从仓库中删除。 

### 版本删除恢复

如果删除本地，没有删除仓库就可以恢复文件，如果本地还有仓库都被删除了就不能恢复了
git checkout README恢复文件

### 版本对比

git diff commitID1 commitID2，把提交的两次文件做一个对比，看一下两者的差异

### patch

patch多指补丁的意思, 在这里更多的指程序有一些bug, 需要我们进行fixed, 那fixed源码文件就是patch.
patch实际上是保存两个文件的差异.
* 生成patch                        
  git format-patch -p1
* git 打patch                     
  git am patch-name  
  
### github分支

github分支就像一个镜像，可以克隆出来以供分支使用，A的分支B就具有A的特性，当B发生变化可以让分支进行合并，分支的作用是促进工作效率。

## 远程仓库
完全可以自己搭建一台运行Git的服务器，不过现阶段，为了学Git先搭个服务器绝对是小题大作。好在这个世界上有个叫GitHub的神奇的网站，从名字就可以看出，这个网站就是提供Git仓库托管服务的，所以，只要注册一个GitHub账号，就可以免费获得Git远程仓库

### 添加远程仓库

如果我们现在本地有一个git仓库, 我们使用remote add 命令将它添加到远程的仓库中.
git remote add origin https://github.com/mkkeliping/stuinfo.git
仓库第一次与远程服务建立需要执行该命令进行连接，https://github.com/mkkeliping/stuinfo.git是仓库的URL，即以后把仓库文件提交的地方。该地址在第一次创建仓库时会显示出来，如果第二次可以从该仓库的CLONE处粘贴该地址。

### 向远程仓库提交
git push origin master
如果我们本地的仓库进行开发, 交进行提交commit. 那么我们本地的仓库和远程的仓库就不能保持同步了.那么我们需要把本地的这次提交也要反映在远程的仓库上. 那么我们就需要使用push命令.
### 远程的仓库的信息更步到本地
git fetch origin
### 删除远程分支
git push [远程名] :[分支名]。 在于分支名前的冒号.
git push -u origin :branch-name
### clone
当我们知道git仓库的地址了(在github上有很多的开源仓库.), 就可以使用下面的命令将源码拉取到本地.
git clone url
### pull
我们已经拉取源码到本地了, 但是服务器上的git已经更新了, 当我们需要将服务器的源码与本地源友进行同步进时, 需要使用下面的命令.
git pull

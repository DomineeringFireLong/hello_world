# 学习git和github使用
## git简介：版本控制的分布式系统。  
集中式：代码放在一个服务器上集中管理，所有操作都需要服务器的支持。  
分布式：从从主仓库拉取一份代码下来后，自己的电脑就是服务器，每个人的客户端（电脑）都是服务器，提交到主仓库时，合并推送到主仓库就可以了。  
    没有一个主版本号的，它们都是用id(哈希算法算出)来做标志的,用master作为主仓库，其它的分支怎么迭代都不会影响到master  
##  git原理  
本地仓库文件到远程仓库的流程：工作区----> 暂存区 ----> 仓库区 ----> 远程仓库   
![git原理](/git原理.png)  
    git init
    git add README.md
    git commit -m "首次提交代码"
    git remote add origin https://github.com/DomineeringFireLong/hello_world.git  
    git push -u origin master   
    查看origin 远程仓库的 URL  
    git remote get-url origin  
    查看所有远程仓库的详细信息  
    git remote -v  
    # 删除现有的 origin 远程仓库   
    git remote remove origin  
    # 重新添加 origin 远程仓库   
    git remote add origin https://github.com/DomineeringFireLong/hello_world.git  
    #覆盖现有远程仓库   
    git remote set-url origin https://github.com/DomineeringFireLong/hello_world.git  

##  github：代码托管、版本控制、协作开发的社区。
代码上传到 GitHub 后，会保存在 GitHub 的服务器上，不占用本地存储空间。  

## 常用命令：
1.配置git环境：  
    创建项目的SSH Key
    git config --global user.name "你的用户名"    
    git config --global user.email "你的邮箱"      
    ssh-keygen -t rsa -C "你的邮箱"  
    ssh（Secure Shell）是一个远程登录服务器或设备的加密网络协议
2.创建本地空仓库  
    git init    
    master  
    初始化后会生成git的配置文件目录，普通的"ls"命令是看不到的，我们需要使用ls -ah查看隐藏目录.  
3.新建文件添加到本地仓库  
    将文件添加到缓存区: git add   
        提交到本地仓库:git commit -m "描述信息"  
    head->master 代表这次提交到master主仓库  
        重写上一次的提交信息:git commit --amend  
4.查看历史提交日志  
git log  
git log --pretty=oneline  
    简洁输出  
5.回滚代码仓库  
    git reset --hard 重置代码仓库版本id     
        有三种模式  
        --soft 、--mixed以及--hard是三个恢复等级。  
        使用--soft就仅仅将头指针恢复，已经add的暂存区以及工作空间的所有东西都不变。  
        如果使用--mixed，就将头恢复掉，已经add的暂存区也会丢失掉，工作空间的代码什么的是不变的。  
        如果使用--hard，那么一切就全都恢复了，头变，aad的暂存区消失，代码什么的也恢复到以前状态。  
    git reset --hard HEAD^  
        回滚当前仓库指向的上一个版本,^代表上一个版本的意思  
    git reset --hard HEAD~3  
        代表以当前版本为基数，回滚多少次。  
6.查看提交之后文件是否做了改动  
    git status  
    查看当前仓库状态  
    A：未修改  
    AM：修改  
    Untracked：未提交  
    modified：新文件，但未提交  
7.工作区与缓存区  
    工作区：工作区就是你当前的工作目录  
    缓存区：这里存放了你使用git add命令提交的文件描述信息，它位于.git目录下的index文件中  


branch分支
  1.并行开发：在软件开发过程中，多个不同的开发任务同时进行的情况。通过创建不同的分支，不同的开发者或者同一开发者可以在不同分支上独立地进行开发工作，而不会相互影。  
  2.版本管理：分支允许你在项目的不同状态之间进行切换和管理。每个分支都可以有自己独立的提交历史，代表着项目在某个特定方向上的发展。  

blame 
每一行代码的最后修改信息

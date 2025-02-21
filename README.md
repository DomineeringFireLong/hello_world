# 学习git使用
## git简介：版本控制的分布式系统。  
集中式：代码放在一个服务器上集中管理，所有操作都需要服务器的支持。  
分布式：从从主仓库拉取一份代码下来后，自己的电脑就是服务器，每个人的客户端（电脑）都是服务器，提交到主仓库时，合并推送到主仓库就可以了。  
    没有一个主版本号的，它们都是用id(哈希算法算出)来做标志的,用master作为主仓库，其它的分支怎么迭代都不会影响到master  
##  git原理  
本地仓库文件到远程仓库的流程：工作区----> 暂存区 ----> 仓库区 ----> 远程仓库      
![git原理](/git原理.png)    

没有add和commit时，所有的操作都在工作区，没有进入暂存区，更没有进入仓库区.  
一旦add之后，进入暂存区；一旦commit进入了仓库区。     

没有add、没有commit时,用git checkout filename 可以从暂存区恢复文件到工作区.   
有add、没有commit时,用git log 找到commit的最新的id号，git checkout id号 filename 可以从本地仓库的历史信息恢复文件到工作区.  
有add没有commit时,用git log 找到commit的期望恢复的版本id号，git checkout id号 filename 可以从本地仓库的历史信息恢复文件到工作区.  

![恢复原理](/恢复原理.png)     


## git基本组成框架
Workspace：开发者工作区,当前写代码的目录，它一般保持的是最新仓库代码。  
Index：暂存区,位于.git目录中，它用来存放临时动作.  
    选择性提交文件或更改。  
    分阶段构建提交。  
    提供预览和检查更改的机会。  
    确保提交的内容是明确和可控的。  
Repository：仓库区（或本地仓库）    
Remote：远程仓库  

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
    实在不确信哪些文件是改动过的，你只需要使用
        git add --all  
    
4.查看历史提交日志  
    git log  
    简洁输出  
    git log --pretty=oneline   
    查看单个文件可回滚版本：git log filename  
    git reset命令将其回滚就可用  
    查看提交历史  
    git reflog 

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
    
8. 文件撤销回到最近一次修改的状态，vim修改后，想撤销  
    git checkout -- file  
    这个功能本质是切换，不能一直迭代恢复。  
    checkout：切换参数，通常用来切换分支仓库   
    
9.删除文件：git rm  
    git rm删除文件，但是也需要使用git commit提交一次    
    git rm会先将文件放入缓存区,且没有使用commit提交的情况下,git rm后恢复文件：git rm、git reset、git checkout  
    使用git reset重置所有缓存区操作   
    重置完成之后在使用git checkout命令将文件取消操作  

10.git创建分支：git branch、git checkout  
    创建分支并切换过去
    git checkout -b dev
    等价于
    git branch dev
    git checkout dev
    查看当前属于哪个分支，也就是查看HEAD的指向
    git branch   
    查看当前所有分支:git branch -a   
    git删除本地分支:git branch -D 分支名  
    git删除远程分支:git push origin --delete 远程分支名
    git修改分支名称：git branch -m 分支名 新的分支名 
    分支作用
    1.并行开发：在软件开发过程中，多个不同的开发任务同时进行的情况。通过创建不同的分支，不同的开发者或者同一开发者可以在不同分支上独立地进行开发工作，而不会相互影。  
    2.版本管理：分支允许你在项目的不同状态之间进行切换和管理。每个分支都可以有自己独立的提交历史，代表着项目在某个特定方向上的发展。 
 
    
11.git切换分支: git checkout   

12.git合并分支: git merge
    新建分支并做完工作之后，想要把分支提交至master，只需要切换到master仓库，并执行git merge 分支名就可以了  
    git checkout main  # 切换到主分支  
    git merge feature/new-feature  # 将 feature/new-feature 分支合并到当前分支   
    
13.git保存当前工作切换分支：git stash  
    当前工作区修改了文件或者其它功能时，不能切换或者创建到其它分区   
    git stash list查看当前存储了多少工作状态   
    切换上个分支 git stash pop
14将别的分支修改转移到自己的分支：git cherry-pick
    远程仓库已经更新时，本地仓库还没修改，该命令将master改动代码合并到我们分支上，不会修改我们的代码。

15 pull、fetch、merge
    git clone 用于从远程仓库完整复制一个项目到本地,创建一个新的 Git 本地仓库。  
    git pull 用于从远程仓库更新本地仓库的内容。本地仓库已经存在，且需要获取远程仓库的最新更改。  
    git pull origin main  
    git pull 实际上是两个操作的组合：  
    git fetch：从远程仓库下载最新的提交和分支信息，但不会修改本地文件。  
    git merge：将下载的更改合并到当前分支。  
![pull](/pull.jpg)  

注意pull是从远程仓库直接到本地仓库和工作区。
而push是从本地仓库到远程仓库，所以修改的文件要add和commit。
    

#  github：代码托管、版本控制、协作开发的社区。
github、gitlab、gitee等都是远程仓库平台。  
本地仓库通过ssh与远程仓库关联。   
代码上传到 GitHub 后，会保存在 GitHub 的服务器上，不占用本地存储空间。  

##基本使用
1.创建一个ssh的key，因为github是用ssh服务进行通讯的。
ssh-keygen -t rsa -C "your_email@example.com"

2.关联本地和远程仓库
创建本地仓库     
git init   
git add README.md      
git commit -m "首次提交代码"       
git remote add origin git@github.com:DomineeringFireLong/hello_world.git     
origin是远程库的名称   

3.上传代码：本地仓库->远程仓库   
git push -u origin dev   
git push -u origin main   

## 远程仓库->本地仓库    
新建空目录，不需要git init
git clone "http:..."#会自动初始化,默认main分支
git clone -b分支名 仓库地址来指定分支

关联gitee远程仓库  
git remote add gitee git@gitee.com:zhang-zhuojiang/remote-warehouse-test.git  

上述是ssh连接方式，不要用http  
http和ssh本质上都可以推拉代码
https://gitee.com/zhang-zhuojiang/remote-warehouse-test.git   
  
测试远程连接：  
ssh -T git@gitee.com  

上传远程仓库
git push gitee main/dev
查阅帮助信息   
git remote -h

看看关联的远程仓库数量  
git remote -v
git remote show

[//]:gitremoteaddorigin远程仓库URL  

git remote add origin git@github.com:DomineeringFireLong/hello_world.git      
git push -u origin main       
查看origin 远程仓库的 URL   
git remote get-url origin    
查看远程仓库信息  
git remote show origin   
查看所有远程仓库的详细信息    
git remote -v  
删除现有的 origin 远程仓库    
git remote \remove origin   
重新添加 origin 远程仓库      
git remote add origin git@github.com:DomineeringFireLong/hello_world.git  
#覆盖现有远程仓库     
git remote set-url origin git@github.com:DomineeringFireLong/hello_world.git   
重新命名当前分支
git branch -M main


## 提交冲突的解决办法
当远程仓库和本地仓库不一致时，push会产生冲突。
需要首先pull一下最新版本的库，然后再push。

所以，并行开发时，进行各自有各自的分支，且不要同时修改同一个文件。
不过，如果多个人改了同一个文件，合并时Git会标记标出冲突的部分，进行手动改正。

冲突原因：不同的人改了公共的文件，导致远端仓库和某些本地仓库的版本不一致。

避免方法：划分好各自修改的文件，尽量不要同时改一个文件。  

看文件前后的变化   
git diff 文件

只有一方修改时，通过pull和push可以完成对齐。
git pull origin main
git push origin main


但是如果两边都改了，就需要手动对齐。
git pull origin main会直接报错
拆成两步：
git fetch origin main
git merge origin main

git就会自动显示冲突的部分，来让我们手动改正。
改正后：git push origin main


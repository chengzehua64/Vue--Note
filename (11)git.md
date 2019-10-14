git是什么：是一个分布式管理版本控制工具
分布式：每个主机都可以独立运行，互不影响，最终也可协作来完成某件事情的模式示例：git集中式：有一个中心主机来管理，存在依赖关系例如：SVN

 git和git仓库关系
安装git客户端软件：
Windows：https：//gitforwindows.org/

苹果机：https：//git-scm.com/download/mac

git常用命令：
1.初始化git：git init

 注：在项目根目录下产生一个.git文件
2.添加：git add文件名

例如：git add index.html

  注意：通常提交哪个文件就add哪个文件，不要全部提交！！！！！！！！！！
3.查看文件状态：git status

4.提交本地仓库：git commit -m'提交的说明文字'

 例如：git commit -m '创建了index.html和a.js文件'
5.查看提交的历史记录：git log

   简化写法： git log --pretty=oneline
6.历史回退

利用git将项目推进到远程仓库
远程仓库：国内（例如：码云），国外：github，gitlab

以github例：

1.先注册或登录github
2.在本地生成公钥和密钥对

  ssh-keygen -t rsa -b 4096 -C "hjl@aaaa.com"

  通常生成2个文件，存放在c:/Users/你的用户名/.ssh/

    id_rsa
    id_rsa.pub (放到远程仓库上)

    settings->ssh-new sshkey-->输入标题和id_rsa.pub内容

3.测试连通

  ssh -T git@github.com

 最后：You've successfully 

4.连接远程
git remote add origin远程仓库地址

仓库地址：

 ssh:   git@github.com:w3cteching/gitlesson.git

 https: https://github.com/w3cteching/gitlesson.git

 如何查看连接的仓库信息：git remote -v

 删除连接的仓库地址：git remote rm origin


 git remote参考资料：http://www.ruanyifeng.com/blog/2014/06/git_remote.html

 注意：如何出现git pull不能拉取下来，可以通过下面的命令来解决：

 git pull origin master --allow-unrelated-histories


5.推送 

git push -u origin master
================================

1.使用git流程：git add，git commit，git push

拉取项目：

 第一次：git clone 远程克隆仓库的地址

  例如：git clone git@github.com:w3cteching/vue-pull-to.git

 第二次：git pull
2.工作区，暂存区，本地仓库，远程仓库的关系？？？

工作区-git add->暂存区-git commit->版本库-git push->远程仓库

git add

git commit 

git push
3.分支管理：【重点】主要用于团队成员之间的协作管理

  1.查看分支：git branch

     注：默认用git branch查看时，只有一个master主分支

     通常master分支是最终发布产品的分支,该分支不是开发分支

  2.创建分支：git branch 分支名

  3.切换分支：git checkout 要切换的分支名

    注：
    
       1.即创建也切换的命令：git checkout -b 新的分支名

       2.没有被add,commit的分支是没有切换到其他分支上的

     

  4.合并分支：git merge 要合并的分支

  5.合并分支出现冲突如何解决？？？？

     适用场景：多人在不同分支上修改同一个文件时，会产生合并冲突
     解决方案：手动解决，然后再add,commit，再push推送到远程

  6.删除分支：

     git branch -d 要删除的分支名  //删除已经合并的分支

     注意：
     
        1.不能在当前分支上删除当前分支
        2.通常不能删除未合并的分支，那如果删除未合并的分支，用-D

          git branch -D 要删除的分支


  7.可视化git操作

  git可视化软件：  sourcetree，或通过编辑器内置git来实现可视化


==============================================================

一、复习一下分支管理：

   查看分支：git branch

   创建分支：git branch 分支名 

   合并分支：git merge 

   删除分支：git branch -d 或 /-D 要删除的分支名
二，继续分支学习

1.如何将本地分支提交到远程仓库：

   git push origin 要提交的分支名

   注：若出现提交不上分支，则先设置一下跟踪轨迹：

       git push --set-upstream origin 要提交的分支名

  2.删除远程分支：

   git push origin :要删除的分支名

  3.tag管理：即版本管理

   查看tag: git tag

   创建tag: git tag tag版本名  //默认打在最近的一次commit id上

    注：可以打在指定的commit id上，
    
    格式： git tag tag版本名 commit_id

    例如：git tag v0.1.0 ca641b4

  4.删除tag:

    本地tag删除：git tag -d 要删除的tag名

    远程tag删除：git push origin :要删除的tag名


  5.如何利用git协作完成项目：git flow

  协作流程：http://www.ruanyifeng.com/blog/2015/12/git-workflow.html
  git远程操作:http://www.ruanyifeng.com/blog/2014/06/git_remote.html

  mint ui:http://mint-ui.github.io/#!/zh-cn
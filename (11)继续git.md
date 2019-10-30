1.使用git流程：git add ,git commit , git push

拉取项目：

 第一次：git clone 远程克隆仓库的地址

  例如：git clone git@github.com:w3cteching/vue-pull-to.git

 第二次：git pull
2.工作区，暂存区，本地仓库，远程仓库的关系？？？

工作区-git add ->暂存区 -git commit ->版本库-git push->远程仓库

git add

git commit 

git push
3.分支管理：【重点】主要用于团队成员之间协作管理

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
二、继续分支学习

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
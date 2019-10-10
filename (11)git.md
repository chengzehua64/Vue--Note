git是什么：是一个分布式管理版本控制工具
分布式：每个主机都可以独立运行，互不影响，最终也可协作来完成某件事情的模式 例如：git 集中式：有一个中心主机来管理，存在依赖关系 例如：SVN

 git和git仓库关系
安装git客户端软件：
windows:https://gitforwindows.org/

mac: https://git-scm.com/download/mac

git常用命令:
1.初始化git:git init

 注：在项目根目录下产生一个.git文件
2.添加：git add 文件名

例如：git add index.html

  注意：通常提交哪个文件就add哪个文件，不要全部提交！！！！！！！！！！
3.查看文件状态：git status

4.提交本地仓库：git commit -m '提交的说明文字'

 例如：git commit -m '创建了index.html和a.js文件'
5.查看提交的历史记录:git log

   简化写法： git log --pretty=oneline
6.历史回退

利用git将项目推送到远程仓库
远程仓库：国内(例如：码云)，国外：github,gitlab

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
git remote add origin 远程仓库地址

5.推送 

git push -u origin master
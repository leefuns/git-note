ubuntu 14.04安装git  
apt-get install git
<br/>
尝试连接github  
ssh -T git@github.com
<br/>
ssh-keygen -t rsa -C “email”
公钥文件复制进SSH key中
<br/>
把目录变成GIT管理仓库
git init
<br/>
git add readme.txt
把readme.txt放到Git仓库
<br/>
git commit -m "wrote a readme file"
把文件提交到仓库 -m 后面接本次提交的说明
<br/>
commit可以一次提交很多文件 可多次add不同的文件
<br/>
git status
查看仓库当前状态
<br/>
git diff readme.txt
git diff 接文件名 查看文件具体修改了哪些内容
<br/>
git log
查看文件历史修改记录
<br/>
git log --pretty=oneline
加上参数则显示历史记录的修改版本号和修改说明
<br/>
git reset --hard HEAD^
HEAD表示当前版本 上一个版本是HEAD^ 上上版本是HEAD^^ 往上100个版本HEAD-100
<br/>
这时候执行git log最新那个版本已经不在了 如果还需要最新的版本 
那么就需要找到版本号 执行
git reset --hard 3652342
版本号只需前几位即可 前提是没有关闭命令行
<br/>
git reflog
查看每一条执行的命令
找到版本号随意切换到哪个版本
<br/>
git diff HEAD -- readme.txt
查看工作区与版本库里面最新版本的区别
<br/>
git checkout -- readme.txt
把文件在工作区的修改全部撤销
<br/>
git reset HEAD readme.txt
可以把暂存区的修改撤销掉重新放回工作区
<br/>
rm filename 
工作区删除文件
<br/>
版本库删除文件
git rm filename 并且 git commit
git rm test.txt
git commit -m "remove test txt"
<br/>
工作区文件删错了 从版本库中恢复
git checkout -- filename
git checkout 用版本库里的版本替换工作区的版本 无论工作区是修改还是删除
<br/>
本地仓库关联github远程仓库
git remote add origin git@github.com:leefuns/git-note.git
<br/>
本地库的内容推送到远程库上 第一次推送需要加上参数-u
git push -u origin master
实际上是把当前分支master推送到远程
后面推送提交之后执行
git push origin master
<br/>
push出错执行下面操作
git pull --rebase origin master

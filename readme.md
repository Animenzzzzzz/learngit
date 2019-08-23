
版本库详解

![Image text](https://www.liaoxuefeng.com/files/attachments/919020037470528/0)

HEAD 指向的版本就是当前版本
HEAD 指向的就是当前分支
master 指向最新的提交

git init 初始化仓库

git add <file file1 file2> 添加文件到缓存

git commit -m <message> 提交文件到分支

git status 查看工作区状态

	modified : 被修改的
	untracked : 未追踪

git diff <file> 查看修改内容
git diff HEAD -- <file> 命令可以查看工作区和版本库里面最新版本的区别

git reset --hard commit_id/HEAD^/HEAD~1 切换工作区版本

git log --pretty=oneline	查看提交历史
git log --graph --pretty=oneline --abbrev-commit	分支合并图

git reflog	查看命令历史


撤销修改

git checkout -- <file>

	1.暂存区：移出暂存区，保留修改
	2.工作区：还原至版本库

git reset HEAD <file>	移出暂存区，保留修改


删除文件

git rm <file>	从版本库中删除该文件


远程库

git remote rm origin	移除已关联的远程库

git remote add origin git_url	管理新远程库

git remote -v	查看远程库信息

ssh-keygen -t rsa -C "youremail@example.com" 生成SSH Key

git remote add origin git_url 关联远程库

git push -u origin master	第一次推送master分支的所有内容

git push origin master	推送最新修改

git clone git_url 克隆远程库到本地


分支管理

	Fast forward模式，但这种模式下，删除分支后，会丢掉分支信息.
	禁用Fast forward模式，Git就会在merge时生成一个新的commit (--no-ff)

git branch	查看分支

git branch <name>	创建分支

git checkout <name>	切换分支

git checkout -b <name>	创建+切换分支

git merge <name>	合并某分支到当前分支

git branch -d <name>	删除分支


BUG 分支

git stash 当前工作区暂存的文件储藏并隐藏，防止提交

git stash pop	回到工作现场

git cherry-pick <commit_id>	把bug提交的修改“复制”到当前分支

git branch -D <name>	强行删除未合并过的分支


多人协作

master	分支是主分支，因此要时刻与远程同步；

dev	分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步；

bug	分支只用于在本地修复bug，就没必要推到远程了，除非老板要看看你每周到底修复了几个bug；

feature	分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发。

流程

	1.首先，可以试图用git push origin <branch-name>推送自己的修改；

	2.如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；

	3.如果合并有冲突，则解决冲突，并在本地提交；

	4.没有冲突或者解决掉冲突后，再用git push origin <branch-name>推送就能成功！

如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream-to <branch-name> origin/<branch-name>。

git rebase	操作可以把本地未push的分支提交历史，整理成直线


标签管理

git tag <tagname>	默认为HEAD，也可以指定一个commit id

git tag -a <tagname> -m <message>	指定标签信息

git tag	查看所有标签

git push origin <tagname>	推送一个本地标签

git push origin --tags	推送全部未推送过的本地标签

git tag -d <tagname>	可以删除一个本地标签

git push origin :refs/tags/<tagname>	可以删除一个远程标签


自定义Git

git config --global color.ui true	Git显示颜色

忽略特殊文件

.gitignore

git add -f <file>	强制添加到Git

git check-ignore -v <file>	针对文件检查规则

配置别名

git config --global alias.st status

git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

配置文件

.git/config 

[core]
    ******
[remote "origin"]
    ******
[branch "master"]
    ******
[alias]
    ******
[user]
	name  = *****
	email = *****
	
其他：
	https://gitee.com/liaoxuefeng/learn-java/raw/master/teach/git-cheatsheet.pdf







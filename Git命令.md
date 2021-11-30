Git命令
git config --global user.name 叉叉叉
git config --global user.email 叉叉叉
（存在--global表示是全局配置，不存在表示是局部配置，局部配置表示仅在当前本地仓库有效）
git config --list(查看配置信息)
git init(初始化本地仓库)
git status(查看文件版本控制，查看某一文件当前的状态)
git status -s(同上，简洁版)

git add 文件名(添加单个文件到暂存区)

git add(将当前目录下所有修改添加到暂存区，除按照规则忽略的之外)

git commit(如果暂存区有文件，则将其中文件提交到本地仓库)

git commit -m '评论信息'

git log(显示所有提交的历史记录)

git log --pretty=oneline(单行显示提交历史记录的内容)

git reset --hard 'commit_id'(会退到commit_id指定的提交版本)

git reflog(获取到操作命令的历史)

git reset --hard 'reflog获取到的id'(回到未来的某个提交)

git checkout '被物理删除的文件名'（恢复本地仓库文件夹中被物理删除的文件）

git rm '文件名'(删除在本地仓库中提交过的文件)

vim .gitignore(创建忽略文件,“i”进行插入，“ESC”退出编辑，“Shift”+“zz”确认)

git branch(查看本地分支信息)

git branch -v(查看相对详细的本地分支信息)

git branch -av(查看包括远程仓库在内的分支信息)

git branch dev(新建一个名称为dev的分支)

git checkout dev(新建完dev分支以后，通过命令切换到dev分支)

git checkout  -b dev(新建dev分支，并且切换到该分支上)

git merge dev(将dev分支的修改合并到master分支，前提是当前正在处于master分支中)

git add ./(解决冲突以后的添加代码，之后仍然需要commit操作)

git branch -d dev(删除dev分支)

ssh-keygen -t rsa(git bash执行命令，生成公钥和私钥)

执行完命令后，在window本地用户.ssh目录C:\Users\用户名.ssh下面生成公钥和私钥

git remote -v(查看已经配置的远程仓库服务)

git remote add origin your_remote_git_rope(为本地仓库添加远程仓库)

git push -u origin master(第一次推送时使用，可以简化后面的推送或者拉取命令使用)

git push origin master(将本地master分支推送到origin远程分支)

git fetch origin master/git pull origin master(二者都是用来获取远程仓库的内容)

- git fetch 是仅仅获取远程仓库的更新内容，并不会自动合并
- git pull 在获取远程仓库内容后，会自动做合并，可以看成是git getch 之后 git merge

git remote rm <shortname>(与远程仓库断开连接)

git clone(从远程仓库克隆  支持https和ssh协议)

	1.git配置
	2.
	git diff 比较的是工作目录中当前文件和暂存区域快照之间的差异,也就是修改之后还没有暂存起来的变化内容。	
	若要看已经暂存起来的文件和上次提交时的快照之间的差异,可以用git diff --cached命令

	git commit 这种方式会启动文本编辑器以便输入本次提交的说明。
	(默认会启用 shell 的环境变量 $EDITOR 所指定的软件,一般都是 vim 或 emacs。
	也可以使用git config --global core.editor命令设定你喜欢的编辑软件。)
	
	git commit -m （-m 参数后跟提交说明的方式）
	Git 提供了一个跳过使用暂存区域的方式,只要在提交的时候,给git commit加上-a选项,Git 就会自动把所有已经跟踪过的文件暂存起来一并提交
	
	
	git rm 文件名
	如果删除之前修改过并且已经放到暂存区域的话,则必须要用强制删除选项-f
	git rm --cached 文件名
	
	git mv就相当于运行了下面三条命令:
	$ mv README.txt README
	$ git rm README.txt
	$ git add README
	
	
	查看历史提交：
	
	git log
	git log -p -2 内容差异
	git log --stat 仅显示简要的增改行数统计
	git log --pretty选项,可以指定使用完全不同于默认格式的方式展示提交历史
	git log --since=2.weeks
	git log --author=zhuchao
	
	
	使用图形化工具查阅提交历史 gitk
	
	修改提交
	git commmit -m ""
	git add
	git commit --amend 重新修改提交
	
	取消暂存
	git reset HEAD file
	取消修改
	git checkout file
	
	git reset --hard SHA1码
	
	
	查看远程库
	git remote
	git remote -v 显示克隆地址
	
	
	添加远程库 git remote add [shortname] [url]
	git fetch shortname 
	fetch命令只是将远端的数据拉到本地仓库，并不合并到当前工作分支。
	git pull是从远端仓库抓取数据后并合并到当前工作分支
	
	查看远程仓库信息
	git remote show 远程分支名
	删除重命名
	git remote a b
	git remote rm a
	
	
	
	
	git mergetool 界面修改冲突
	
	
	
	git push:
	
	$ git push <远程主机名> <本地分支名>:<远程分支名>
	
	$ git remote add origin ssh://git@dev.lemote.com/rt4ls.git 
	  origin指向ssh://git@dev.lemote.com/rt4ls.git，origin可以理解为后者的别名
	$ git push origin master:master 
	
	$ git push origin test:master         // 提交本地test分支 作为 远程的master分支
	$ git push origin test:test           // 提交本地test分支作为远程的test分支
	$ git push origin :test              // 刚提交到远程的test将被删除，但是本地还会保存的
	
	
	
	本地分支和远端远端分支对应关系 git branch -vv （.git/config文件）
	本地分支和远端分支 git branch -a 
	远端分支 git branch -r
	远端分支对应的url git remote -v 
	
	HEAD是当前分支  master是最新一次的提交
	
	
	commit后
	git format-patch -1
	git diff id1 id2 >name.patch
	git apply name.patch
	
	
	

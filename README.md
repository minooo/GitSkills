### git add file 把你的修改放到暂存区
### git status 查看当前状态，是否有遗漏
### git commit -m "something" 
### git reset --hard + `commit id` 或者 类似于这样的`HEAD@{1}`版本号
### git checkout -- file 把文件在工作区的修改全部撤销，有两种情况
- 修改后还没有放到暂存区
- 文件已经添加到暂存区，又了修改，如果撤销就回到添加暂存区后的状态
- 如果已经提交，则使用版本回退来达到撤销修改的目的。

### git reset HEAD file 撤销当前的提交暂存区(git add)命令
### git log --pretty=oneline 显示从最近到最远的提交日志，可以以此回到过去
### git reflog 查看“提交命令”历史，可以以此回到未来。


### 推送到远程仓库 `git push -u origin master`
实际上是把当前分支 `master` 推送到远程。由于远程库是空的，第一次推送`master`分支时，  
加上了`-u`参数，

### 最好的方式是先创建远程库，然后从远程库克隆。
创建时记得勾选`Initialize this repository with a README`,这样GitHub会自动  
为我们创建一个`README.md`文件。

### 下一步用`git clone`克隆一个本地库
```js
git clone git@github.com:minooo/GitSkills
...自动完成克隆...
```
也许你还注意到，GitHub给出的地址不止一个，还可以用`https://github.com/minooo/GitSkills.git`  
这样的地址，实际上，Git支持多种协议，默认的`git://`使用ssh，但也可以使用`https`等其他协议。  
注意，使用`https`除了速度慢以外，有个最大的麻烦就是 **每次推送必须输入账号密码** ，但是在某些  
只开发http端口的公司内部就无法使用`ssh`协议而只能使用`https`。

### 分支相关
- 查看分支：`git branch`
- 创建分支：`git branch <name>`
- 把创建的分支推送到远程服务器：`git push origin dev`
- 切换分支：`git checkout <name>`
- 创建+切换分支：`git checkout -b <name>`
- 合并某分支到当前分支：`git merge <name>`
- 不用快速合并：`git merge --no-ff -m "merge with no-ff" dev` 这是有记录的合并，推荐这个
- 删除分支：`git branch -d <name>`
- 强行删除：`git branch -D <name>` 用于删除一个没有被合并过的分支。
- 删除远程分支 `git push origin --delete dev`
- 查看分支提交详细命令：`git log --graph --pretty=oneline --abbrev-commit`
- 查看分支合并图：`git log --graph`
- 一口气提交所有！ `git add --all`
- 强制当前提交推送到远程 `git push -f origin master`  
### 让git对大小写敏感 `git config core.ignorecase false  `

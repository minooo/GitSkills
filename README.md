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

### 文件处理
- 删除某个文件 `git rm test.txt`, 然后保存 `git commit -m "del"`, 如果你删错了也可以恢复 `git checkout -- test.txt`

### 临时处理 master bug，当前分支 dev 还在开发中，怎么办
首先存储现场 `git stash` ，然后切到master处理bug, (最好在master另起一个分支解决），解决完bug后，合并到主分支，  
删除bug分支后，切到dev 分支，重新开启当前开发任务，`git stash list`     
还原现场有两种方式：
- `git stash apply`,但是stash 内容不删除，可以使用 `git stash drop` 来删除
- `git stash pop` 恢复的同时把stash内容也删除了。
如果你多次 stash，先用 `git stash list` 查看，然后恢复指定的 stash, `git stash apply stash@{0}`

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
- 强制覆盖本地 首先： `git fetch --all` ，其次：`git reset --hard origin/master` 

### 异常处理
- 让git对大小写敏感 `git config core.ignorecase false `
- 拉取远程，或者切换分支时如果出现文件未跟踪错误 `git reset --hard origin/master`
* windows使用git时出现：warning: LF will be replaced by CRLF
    * 首先删除当前目录下的 `.git` 文件 `rimraf .git`
    * 禁用自动转换 `git config --global core.autocrlf false`
    * 重新初始化 `.git` 文件。`git init`
    * 之后再次提交你的代码 `git add --all` ...

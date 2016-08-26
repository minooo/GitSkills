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

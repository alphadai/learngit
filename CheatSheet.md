
##### 查看所有的配置以及它们所在的文件：
~~~
$ git config --list --show-origin
~~~
 

##### 三种等价的方法可以找到 Git 命令的综合手册（manpage）：
~~~
$ git help <verb>
$ git <verb> --help
$ man git-<verb>
~~~
>如果你不需要全面的手册，只需要可用选项的快速参考，那么可以用 -h 选项获得更简明的 ``help'' 输出：
~~~
$ git <verb> -h
~~~


##### 检查当前文件状态
~~~
$ git status
~~~

##### 忽略文件
~~~
在.gitignore文件中指定忽略文件

GitHub 有一个十分详细的针对数十种项目及语言的 .gitignore 文件列表， 你可以在 https://github.com/github/gitignore 找到它。
~~~

##### 查看已暂存和未暂存的修改
~~~
$ git diff           // 查看工作目录中当前文件和暂存区域快照之间的差异。 也就是修改之后还没有暂存起来的变化内容。
$ git diff --staged  // 查看已暂存的将要添加到下次提交里的内容
~~~

##### 移动文件
~~~
$ git mv file_from file_to
~~~

##### 查看提交历史
~~~
$ git log              // 按时间先后顺序列出所有的提交
$ git log -p -2        // -p它会显示每次提交所引入的差异 , -2 选项来只显示最近的两次提交
$ git log --stat       // 查看每次提交的简略统计信息
$ git log --pretty=oneline
$ git log --pretty=format:"%h - %an, %ar : %s"
$ git log --graph
$ git log --pretty="%h - %s" --author='Junio C Hamano' --since="2008-10-01" \
   --before="2008-11-01" --no-merges -- t/
~~~

###### 撤消操作
~~~
$ git commit --amend
$ git reset HEAD <file>
~~~

##### 远程仓库的使用
~~~
获取远程仓库
$ git clone https://github.com/schacon/ticgit

显示远程仓库
$ git remote -v

添加远程仓库
$ git remote add pb https://github.com/paulboone/ticgit

从远程仓库中抓取与拉取，不覆盖本地工作区
$ git fetch <remote>

从远程仓库中抓取与拉取，merge到本地工作区
$ git pull

当你想要将 master 分支推送到 origin 服务器时
$ git push origin master

将本地得featureB推送到远程的featureBee，并设置featureB关联featureBee
$ git push -u origin featureB:featureBee


远程仓库的重命名与移除
$ git remote rename pb paul

$ git remote remove paul
~~~

##### 打标签
~~~
列出标签
$ git tag

创建标签 --- Git 支持两种标签: 轻量标签（lightweight）与附注标签（annotated）。
附注标签
$ git tag -a v1.4 -m "my version 1.4"

轻量标签
$ git tag v1.4-lw

后期打标签
$ git tag -a v1.2 9fceb02

共享标签 --- 默认情况下，git push 命令并不会传送标签到远程仓库服务器上
$ git push origin <tagname>。
$ git push origin --tags

删除标签
git tag -d <tagname>
注意上述命令并不会从任何远程仓库中移除这个标签，你必须用 git push <remote> :refs/tags/<tagname> 来更新你的远程仓库
$ git push origin :refs/tags/v1.4-lw

$ git push origin --delete <tagname>

检出标签
如果你想查看某个标签所指向的文件版本，可以使用 git checkout 命令， 虽然这会使你的仓库处于“分离头指针（detached HEAD）”的状态——这个状态有些不好的副作用.

那么通常需要创建一个新分支：
$ git checkout -b version2 v2.0.0
Switched to a new branch 'version2'
~~~

##### 变基
* 总的原则是，只对尚未推送或分享给别人的本地修改执行变基操作清理历史， 从不对已推送至别处的提交执行变基操作，这样，你才能享受到两种方式带来的便利。



#### Git 工具
* 如果你在引用的尾部加上一个 ^（脱字符）， Git 会将其解析为该引用的上一个提交。
~~~
假设d921970为一个合并提交；

$ git show d921970^   
显示d921970的第一个父提交，第一父提交是你合并时所在分支（通常为 master）


$ git show d921970^2
显示d921970的第二父提交，第二父提交是你所合并的分支（例如 topic）


~~~
* 另一种指明祖先提交的方法是 ~（波浪号）, 同样是指向第一父提交,而区别在于你在后面加数字的时候。 HEAD~2 代表“第一父提交的第一父提交”，也就是“祖父提交”

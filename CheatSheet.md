
##### 你可以通过以下命令查看所有的配置以及它们所在的文件：
~~~
$ git config --list --show-origin
~~~
 

##### 若你使用 Git 时需要获取帮助，有三种等价的方法可以找到 Git 命令的综合手册（manpage）：
~~~
$ git help <verb>
$ git <verb> --help
$ man git-<verb>
~~~
如果你不需要全面的手册，只需要可用选项的快速参考，那么可以用 -h 选项获得更简明的 ``help'' 输出：
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
$ git diff           # 查看工作目录中当前文件和暂存区域快照之间的差异。 也就是修改之后还没有暂存起来的变化内容。
$ git diff --staged  # 查看已暂存的将要添加到下次提交里的内容
~~~
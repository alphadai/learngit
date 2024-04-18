# Git cheat sheet

## Reference 
  [廖雪峰的git教程](https://www.liaoxuefeng.com/wiki/896043488029600)    :thumbsup:


## 1. Install git

### 1.1 Install on linux 

~~~
$ git
The program 'git' is currently not installed. You can install it by typing:
sudo apt-get install git 
~~~

### 1.2 Install on mac
~~~
reference to http://brew.sh/ see how install by homebrew
~~~

### 1.3 Install on windows
~~~
download form https://www.liaoxuefeng.com/wiki/896043488029600 and install 
~~~


## 2 Config git

~~~
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
~~~


## 3. Create local repository

~~~
$ mkdir learngit
$ cd learngit
$ pwd
/Users/michael/learngit
~~~

~~~
$ git init
Initialized empty Git repository in /Users/michael/learngit/.git/
~~~

## 4. create remote repository

~~~
create ssh key on local machine, add these key to remove server(github for example)
$ ssh-keygen -t rsa -C "youremail@example.com"
~~~

~~~
create remote repository on remote server(github for example)
~~~

~~~
$ git remote add origin git@github.com:michaelliao/learngit.git
~~~

~~~
$ git push -u origin master
Counting objects: 20, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (15/15), done.
Writing objects: 100% (20/20), 1.64 KiB | 560.00 KiB/s, done.
Total 20 (delta 5), reused 0 (delta 0)
remote: Resolving deltas: 100% (5/5), done.
To github.com:michaelliao/learngit.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
~~~
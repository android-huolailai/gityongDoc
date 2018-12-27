## 常用git命令

#### 常规操作

+ ```git init ```     创建git库，生成.git文件
+ ```git clone  <远程仓库地址>```      克隆远端master分支
+ ```git clone -b <指定分支名> <远程仓库地址> ```   克隆远端指定的分支

#### 关于远端

+ ```git remote ``` 查看远程主机
+ ```git remote -v ``` 查看远程主机地址

#### 创建分支

+ ```git branch 2.0.1.20120806```    创建本地分支（在哪个分支下创建既基于那个分支）
+ ```git checkout -b develop  origin/develop```  根据远程分支check分支
+ ```git checkout release/3.8.0 ```    可以直接check远端的分支（作用同上）
+ ```git push <远程主机名> <本地分支名>:<远程分支名> ```  提交代码到远程主机（如果远程分支没有则会新建分支）

#### 删除分支

+ git branch -d  BranchName    删除本地分支

+ ```git branch -a
   remotes/origin/HEAD -> origin/master
    remotes/origin/debugFD
    remotes/origin/develop
    remotes/origin/feature/Rockchip_x3399
    remotes/origin/feature/face
    remotes/origin/master
  ```

  ```git push origin --delete feature/face ```       删除远端分支

### 查询分支

+ ```git branch -a ```    查看所有分支(本地+远端)
+ ```git remote show origin```     查看远程分支

#### 查询本地分支与远端的关联关系

+ ```git branch -vv```

#### 切换分支

+ ```git checkout branch``` （可切换本地已存在分支，也可下载远端分支）

#### 合并分支

+ ```git  merge dev```   将dev分支合并到当前分支

#### 将本地分支与远端绑定

+ ```git branch --set-upstream-to=origin/feature/face    feature/face```

----

#### 提交代码

+  ```git add -A```  提交所有变化
+  ```git add -u```  提交被修改(modified)和被删除(deleted)文件，不包括新文件(new)
+ ```git add . ``` 提交新文件(new)和被修改(modified)文件，不包括被删除(deleted)文件
+ ```git commit -m ""```  提交文案
+ ```git push origin test:test```    提交本地test分支作为远程的test分支
+ ```git push origin test:master```   提交本地test分支作为远程的master分支

----

#### 关于submodule

+ ```git submodule add git@github.com:jjz/pod-library.git   pod-library ```  添加子module pod-library（主工程会多出个.gitmodules文件用来记录submodule信息，同时需要在setting.gradle中添加该module即可）

+ ```git clone <repository> --recursive```      递归的方式克隆整个项目（如果一个工程包含submodule，我们可通过递归克隆将主工程和自工程同时下载下来）

+ 

+ ```
  git submodule init
  git submodule update --remote
  ```

  如果本地工程更新别人提交过子工程的项目，会有.gitmodule文件，执行以上两行代码即可

+ ```git submodule foreach git pull```      在主工程执行会拉取所有子模块代码

+ ```git config -f .gitmodules submodule.TuyaSmart_AppShell.branch release/v3.8.0r107```
  (将submodule更新后     主工程的.gitmodule更新，release/v3.8.0r107表示submodule的最新版本。我们也可以先更新该文件然后建一个task读取该文件的branch，在拉取branch指定的分支)








---
typora-copy-images-to:./
---

# Git

#### 1 git chone克隆项目

```shell
git clone https://github.com/BroMiaoY/design-pattern.git
```

#### 2 将代码推送到已有的空项目

```shell
# 终端初始化git
git init

# 将所有文件代码从工作区添加到暂存区
git add *

# commit到本地仓库
git commit -m "first commit"

# 进入分支
git branch -M main

# 与远程建立连接
git remote add origin https://github.com/BroMiaoY/swust_store.git

# 将分支main推送到远程
git push -u origin main
```

#### 3 github文件夹有白色箭头并且不能打开的解决办法

1. 删除文件子目录下的.git文件夹

2. 从索引中删除文件

   ```shell
   # 从索引中删除文件。但是本地文件还存在， 只是不希望这个文件被版本控制。
   git rm --cached [文件夹名]
   ```

3. 将需要提交的代码从工作区添加到暂存区

   ```shell
   git add [文件夹名]
   ```

4. 将代码推送到本地仓库

   ```shell
   git commit -m "msg"
   ```

5. 将代码推送到远端

   ```shell
   git push origin [branch_name]
   ```

   

#### 4 远端仓库已存在remote origin already exists.

```shell
# 删除关联的origin的远程库
git remote rm origin

# 关联自己的仓库
git remote add origin https://gitee.com/xxxxxx.git

git push origin main
```


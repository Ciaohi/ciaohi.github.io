---
title: git基本操作命令
date: 2019-10-17 12:03:33
tags: [git,github]
---
## 快速开始

[菜鸟教程](https://www.runoob.com/git/git-tutorial.html)


- 生成sshkey，获得仓库管理权限.
- .gitignore把不想上传管理的文件加到这里来
	


### 初始化代码仓库
``` bash
git init
```
### 关联远程仓库
``` bash
git remote add origin 仓库地址
```

### 添加代码
添加到暂存区
``` bash
git add
```

### 提交代码

``` bash
git commit -m "变化信息注释"
```

### 查看日志

``` bash
git log 
```

### 查看详细信息

``` bash 
git show commit id
```




### 上传到远程仓库、强制推送


``` bash
git push
git push -f origin master
```


### 拉取远程代码

``` bash
git pull origin master
```

### 创建分支
``` bash
git branch 名字
```

### 切换分支
``` bash
git checkout 名字
```


### 创建分支并切换到分支
```bash

git checkout -b 名字

```



### 查看远程仓库，以及与本地仓库的关系

``` bash
git remote show origin
```

### 设置远端分支上传
``` bash
git --set-upstream origin 名字
```


### 克隆项目
``` bash
git clone 项目
```


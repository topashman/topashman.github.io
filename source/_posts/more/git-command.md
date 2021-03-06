---
title: Git 命令
date: 2017-12-11 10:31:12
categories: "更多"
tags:
    - Git
keywords: Git
---

这里会简单介绍 Git 操作命令（持续更新……）

<!-- more -->

## git tag

```
$ git tag -h
```

### 新建标签

```
$ git tag -a v0.0.1 -m "version 0.0.1"
$ git tag v0.0.2-light
```

### 标签列表

```
$ git tag
v0.0.1
v0.0.2-light

$ git tag -l
v0.0.1
v0.0.2-light

$ git tag -n1
v0.0.1          version 0.0.1
v0.0.2-light    update xxx
```

### 查看标签详情

```
$ git show v0.0.2-light
```

### 切换到指定标签

```
$ git checkout v0.0.1
```

### 删除标签

```
$ git tag -d v0.0.1
Deleted tag 'v0.0.1' (was bce8bc1)
```

### 为指定 commit 添加标签

```
$ git tag -a v0.0.1-x 77aba8
$ git tag -n1
v0.0.1-x        version 0.0.1-x
v0.0.2-light    update xxx
```

### 提交标签到远程

通常 `git push` 不会将标签提交，需显式操作：

提交 v0.0.1 标签

```
$ git push origin v0.0.1
```

提交本地所有标签

```
$ git push origin --tags
```

## git commit

```
$ git commit -h
```

### amend previous commit

```
$ git commit --amend -h
```

#### 修改上一次提交的 Author 信息

```
git commit --amend --author='Name <email>'
```

符合以上命令格式即可，例如，直接输入上面的命令时

```
$ git log

commit f2928cb0b6bc9d29e533110ad381bd28d9413d8d (HEAD -> master)
Author: Name <email>
Date:   Thu Jan 18 09:54:50 2018 +0800
```

## fatal

### fatal: refusing to merge unrelated histories

- 创建本地仓库
- 创建远程仓库，并自动生成了一些文件
- 需要关联本地和远程仓库，此时无法直接 push
- 首先执行 pull 但是会出现以上报错，添加 `--allow-unrelated-histories` 解决

```
git pull origin master --allow-unrelated-histories
```



---
title: Git
date: 2019-08-01 17:31:25
categories: 工具
tags: Git
---

## 添加或修改用户信息

``` bash
$ git config --global user.name "ring"
$ git config --global user.email "hello@google.com"
```

## 添加仓库地址

``` bash
$ git remote add origin [url]
```

## 修改仓库地址

``` bash
$ git remote set-url origin [url]
```

## 清除缓存

``` bash
$ git rm -r --cached .  (文件名，如果忽略全部 直接用 ".")
$ git add .
$ git commit -m 'update .gitignore'
```

## 分支管理

### 查看分支 
```
git branch    //查看本地分支
git branch -a //查看所有分支
git branch -v //查看各分支最后一个提交对象的信息
```

### 删除分支

```
$ git branch -d testing   		   //删除本地分支
$ git push origin --delete testing //删除远程分支
```
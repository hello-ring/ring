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
$ git remote origin set-url [url]
```

## 清除缓存

``` bash
$ git rm -r --cached .  (文件名，如果忽略全部 直接用 ".")
$ git add .
$ git commit -m 'update .gitignore'
```

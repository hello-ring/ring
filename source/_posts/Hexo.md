---
title: Hexo
date: 2019-08-04 12:11:47
tags: Hexo
---

# Hexo基本使用

## 写文章

### 执行命令
```
hexo new "title"
```

### 编辑文章
执行命令后 在根目录下 source/_posts 中会增加一个文件title.md
打开即可直接编辑(Markdown语法)

### 本地预览
```
hexo server
```
打开浏览器输入 http://localhost:4000 预览效果

### 生成静态文件并且部署
```
hexo d -g
```

hexo g生成静态文件，hexo d部署，hexo d -g 生成文件并部署
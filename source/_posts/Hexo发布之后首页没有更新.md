---
title: Hexo发布之后首页没有更新
date: 2019-01-18 22:38:24
tags:
- Hexo
- Issue
categories:
- [解决方案]
---

今天，在使用`hexo clean && hexo deploy`命令将新创建的文章发布到`Github Pages`时，遇到了首页位置没有更新的问题，文章相关的统计数据也没有更新过来，尝试分开执行这个两个命令：

```bash
$ hexo clean
$ hexo deploy
```
<!--more-->
根据命令行执行的结果来看，`Hexo`有重新生成文件，但是`Github Pages`的首页信息还是没有更新过来，推测缓存没有更新。百度网上是否有相同的情况，有提到需要重新生成文件，暗自推测可能是`hexo generate`命令和`hexo deploy`命令的文件生成有些不同，尝试执行以下命令：

```bash
$ hexo clean && hexo generate
$ hexo deploy
```

终于，在发布成功之后，`Github Pages`首页显示正常了。


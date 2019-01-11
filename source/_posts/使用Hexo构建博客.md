---
title: 使用Hexo构建博客
date: 2019-01-10 22:39:57
tags:
- Tools
- Node
- Hexo
categories:
- [工具]
---

# 前言

忙碌了一年，在这个2019年开始之际，整理和总结上一年的经验和教训，发现并没有多少被记录下来，仅仅只记录做了哪些事，至于其中经验教训，并没有记录多少，因而，决定通过写博客的方式记录下自己的收获，同时也可以和各位网友进行交流。关于写作的博客框架，也看了几个，仔细比较之下发现`Hexo`比较适合我，因为这个框架是基于`Node`，刚好属于比较熟悉的部分，并且使用比较简单。废话不多说，接下来就是博客搭建的过程。

<!--more-->
# 准备

`Hexo`是基于`Node`的，可以通过一条指令部署到`GitHub Pages`、`Heroku`等网站上，因为准备以`Github Pages`的方式部署博客，所以需要安装`Git`。安装清单如下：

1. Node
2. Git
3. Yarn, 可选

如果习惯于`Yarn`来进行`Node`的包管理，建议安装一个`Yarn`，至于`Git`和`Node`的安装过程，可以百度或者到官方网站上查看其安装过程。`Git` 和 `Node` 安装完毕之后，通过执行下面的命令安装`Hexo`命令行客户端：

```bash
npm install hexo-cli -g
```

安装 Hexo 完成后，执行下面的命令，创建 Hexo 的工作目录并安装相应的依赖。

```bash
hexo init <folder> && cd <folder>
npm install # or yarn
```

运行命令 `hexo server`启动本地服务器，可以在 `http://localhost:400` 下看到您的博客，接下来需要部署到 GitHub 上，供外部进行访问。

# 部署到 GitHub Pages

首先，在 GitHub 官网上注册一个账号，使用注册的邮箱地址在本地生成 SSH Keys，`ssh-keygen -t rsa -C 'yourname@email.com'，生成完成后将用户目录下 `.ssh\id_rsa.pub` 文件中的内容复制粘贴添加到 GitHub 设置中。输入下面的命令，测试设置是否成功:

```bash
ssh -T git@github.com
> Hi aierui! You've successfully authenticated, but GitHub does not provide shell access.
```

看到下面的输出，说明设置已经成功。设置成功后，通过 `git config` 命令陪伴 Git个人信息。至此，Git 的配置都已完成，接下来只需配置 `config.yml` 文件，设置部署方式，因为要部署到 GitHub Pages 上，配置如下：

```yaml
# Doc: https://hexo.io/zh-cn/docs/deployment
deploy:
  type: git
  repo: git@github.com:<github-name>/<github-name>.github.io.git
  branch: master
```

因私人仓库的 GitHub Pages 只能识别`master`分支的内容，所以部署的分支必须指定为`master`，至于其他类型的仓库则另当别论了。接下来，执行下面的命令部署本地文件到 GitHub Pages：

```bash
# 删除旧的生成文件，重新部署到 GitHub Pages 上
hexo clean && hexo deploy
```
部署成功后，在浏览器中输入`https://<github-name>.github.io`，会看到了 Hexo 已经成功部署到 GitHub Pages 上了。若部署失败，出现 `error deployer not found: git` 的错误，则是因为没有安装 Git 的扩展插件，执行命令 `npm install hexo-deployer-git --save` 即可。

# 结束语

至此，Hexo 博客框架已经搭建完毕，现在可以通过 `hexo` 命令发布文章了。为了多个设备上管理博客和保存博客项目，可以博客工作空间发布到 Github 上。



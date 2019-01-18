---
title: Go学习笔记(一)起步
date: 2019-01-18 21:29:29
tags:
- Go
categories:
- [编程笔记]
---

## 前言

`Go`是一门静态类型的、支持并发的编译型语言，具备垃圾回收功能，语言风格与`C`有些许类似的地方。比如容器技术`Docker`、分布式服务发现`Consul`就是基于`Go`语言实现，因此，学习`Go`语言有利于了解`Docker`和`Consul`的底层实现机制，可以快速解决项目开发遇到的相关的问题。

## 安装

通过`Go`官网下载本机操作系统支持的安装版本，也可以尝试通过编译源码来安装，因为在家里使用的操作系统是`MacOS`，因而选择通过包安装工具`Homebrew`进行安装，执行`brew install golang`命令就会安装最新版的`Go`环境，安装成功后执行下面的命令，测试安装是否成功。

```bash
$ go version
go version go1.11.4 darwin/amd64
```

<!--more-->
## Warm up

在正式进入`Go`语言的编程知识的学习之前，先上手一个简单的程序来练练手。首先，创建一个`hello.go`文件，写入如下的代码并保存：

```go
package main

import "fmt"

func main() {
	fmt.Printf("Hello, world!\n")		
}
```
然后，使用`Go`命令行工具编译运行它：

```bash
$ go run hello.go
Hello, world!
```

## 环境变量

`Go`工具主要为公共代码中维护的开源代码而设计，因而作为约定，`Go`代码必须放在工作空间内。`Go`工作空间下一般包含三个目录：`src`、`pkg`、`bin`，工作空间的结构如下：

```bash
.
├── bin # 包含编译后的可执行文件
├── pkg # 包含包对象
└── src # Go源码文件，以包的形式组织
```

工作空间的位置通过设置`GOPATH`环境变量来指定，这是在开发`Go`项目之前唯一需要设置的环境变量。

```bash
$ export GOPATH=$HOME/develop
$ export PATH=$PATH:$GOPATH/develop
```

## 结束语

`Go`的并发模型相较于线程模型来说比较简单，使用`Go`语言开发高并发的应用相对来说比较简单，使用`Go`语言进行项目开发是一个有趣的尝试，可以以后的开发过程中进行实践。


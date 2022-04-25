---
layout:     post
title:      "Welcome to Nastul's Blog"
subtitle:   " \"Hello Coding, Hello World \""
date:       2017-01-04 22:00:00
author:     "Nastul"
header-img: "img/post-bg-2015.jpg"
tags:
    - Life
---
> “Cs. ”
> 
Update -08/02/2019 

## 前言

<br>
之前一直用自己的服务器写blog，断断续续的没能一直坚持，自己的服务器也不太有时间维护，刚好赶上快要准备工作了，就花点时间 **github+jeykll** 搭了一个，顺便记录下这段时间学习的内容。(是的，17年在准备工作，然后突然就决定出国继续学习，到现在19年了才又回过头来重新来过博客)

<br>

---
使用了qiubaiying的模板
`git clone git@github.com:qiubaiying/qiubaiying.github.io.git`<br>


jeykll文档
`https://www.jekyll.com.cn/`

<br><br>
基本文件存放位置

- _config.yml 全局配置文件
- _posts	放置博客文章的文件夹
- img	存放图片的文件夹

<br><br>
git 基本操作：

- git add .
- git commit -m ""
- git push
- git config --global user.name "example"
- git config --global user.name "example"


问题：<br>
error:src refspec master does not match any

原因分析：
引起该错误的原因是，目录中没有文件，空目录是不能提交上去的

`touch README`

`git add README `

`git commit -m 'first commit'`

`git push origin master`


问题:
remote: Permission to<br>

原因分析：<br>
需要修改系统的凭据，  control panel -> manage
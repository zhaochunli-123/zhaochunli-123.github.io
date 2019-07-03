---
layout:     post
title:      "博客发文教程"
subtitle:   " \"Blog post tutorial\""
date:       2019-07-02 18:33:00
author:     "张凡"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - 教程
---

> Hello world,hello blog. 


## 1、前言

今天花了一天的时间，博客就这样开通了

该博客的成功搭建，离不开[Hux](https://github.com/huxpro) Github Pages教程的帮助，在此感谢Hux和为了开源而努力的人们，正是因为你们的存在，才使得有更多的人能享受到计算机和互联网带来的便利。


## 2、如何发表自己的博客文章

- 1、在项目首页找到_post文件夹
![](https://chunlioss.oss-cn-beijing.aliyuncs.com/images/post.jpg)
找到_post文件夹后，点击进入

- 2、点击左上角Creat new file建立新文件夹
为了熟悉文件规则，先以已经发表的博文为例，如下图所示，点击打开已发表博文.md文件。
![](https://chunlioss.oss-cn-beijing.aliyuncs.com/images/openpost.jpg)
如下图所示为打开的博文.md文件展示出的效果，如图中红框所示为博文发文的基本框架，包含了博文的很多信息，红框所示表格必不可少。表格下方为博文的正文
![](https://chunlioss.oss-cn-beijing.aliyuncs.com/images/mdfile.jpg)
如下图所示为上图中.md文件在编辑状态下的截图
![](https://chunlioss.oss-cn-beijing.aliyuncs.com/images/editmdfile.jpg)

总之，新建的博文按照第一篇所示的博文的格式来编辑就可以了
## 3、本博客支持的博文格式
### 3.1、段落引用
段落语法如下所示：
```
> 这句话将被引用
```
效果如下所示
> 这句话将被引用
### 3.2、插入图片
插入图片的语法如下所示
```
![图片名称——这部分可留空](图片的网络地址)
例如：![](https://chunlioss.oss-cn-beijing.aliyuncs.com/images/5af27f751eedd9c0.gif)
```
显示效果如下所示：
![](https://chunlioss.oss-cn-beijing.aliyuncs.com/images/5af27f751eedd9c0.gif)
### 3.3、文本链接
如果你想在某段文本中插入链接，就可以使用文本链接。语法如下所示
```
[文本](文本中插入的链接)
例如：[去流浪](https://music.163.com/#/song?id=1344340338)
```
你听过周笔畅唱的流浪地球的主题曲《[去流浪](https://music.163.com/#/song?id=1344340338)》吗？可好听了
### 3.4、插入代码
如果你的博文中需要插入代码，可以使用如下语法使你的代码高亮，显示更美观
```
使用连续的三个上撇号把代码包在中间，其中第一个连续的上撇号后面加上所使用的代码语言，如下所示
    ```所使用的代码语言
    你的代码放在这里
    ```
    举个python代码的例子
    ```python
    import requests   #导入requests模块
    
    headers={"user-agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.131 Safari/537.36"}
    url='http://www.baidu.com'
    req=rwquests.get(url,headers=headers)
    req.encoding=req.apparent_encoding
    if req.status==200:
        text=req.text
    else:
        text=''
        pass
    print(text)
    ```
```
上面所举代码高亮显示效果如下所示
~~~python
    import requests   #导入requests模块
    
    headers={"user-agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.131 Safari/537.36"}
    url='http://www.baidu.com'
    req=rwquests.get(url,headers=headers)
    req.encoding=req.apparent_encoding
    if req.status==200:
        text=req.text
    else:
        text=''
        pass
    print(text)
~~~
### 3.5、插入无序列表
插入无序列表的语法如下所示
```
无序列表使用*或+或-标识
例如：
- 我是第一个无序列表
- 我是第二个无序列表
- 我是第三个无序列表
```
效果如下所示：
- 我是第一个无序列表
- 我是第二个无序列表
- 我是第三个无序列表
### 3.6、插入有序列表
插入有序列表的语法如下所示
```
有序列表为数字+小数点
例如：
1. 我是第一个有序列表
2. 我是第二个有序列表
3. 我是第三个有序列表
```
效果如下所示：
1. 我是第一个有序列表
2. 我是第二个有序列表
3. 我是第三个有序列表
### 3.6、插入表格
插入表格的语法如下所示：
```
大学|录取最低分|录取平均分|录取人数
-|-|-|-
清华大学|679|685|32
北京大学|680|687|35
北京航空航天大学|650|656|38
```
显示效果如下所示：
|大学| 清华大学|北京大学|
|录取分数:|680|680|
## 结语
希望你能喜欢这个专属于你的博客网站，赵春丽。
你可以在这里面发表你的感想、影评书评、笔记、摄影作品、学习历程等等，祝你使用愉快

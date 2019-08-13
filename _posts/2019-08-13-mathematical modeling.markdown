---
layout:     post
title:      "mathematical modeling"
subtitle:   " \"数学建模竞赛\""
date:       2019-08-13 6:48:00
author:     "赵春丽"
header-img: "https://chunliblog.oss-cn-beijing.aliyuncs.com/images/%E7%94%9F%E6%9C%BA%E5%B0%8F%E6%B5%B7%E8%B1%9A.jpg"
catalog: true
tags:
- champion
---

## 数据建模常规的MATLAB实现

### 1.1 数据的读入与读出

#### 1.1.1 EXCEL与 MATLAB 的数据交互

1.我的EXCEL中没找到加载宏选项

#### 1.1.2 记事本与 MATLAB 的数据交互

1.我在桌面创建的记事本，在MATLAB中用load就会显示错误

``` MATLAB
a=load(figure.doc) 

未定义变量 "figure" 或类 "figure.doc"。
出错 f7 (line 1)
a=load(figure.doc)
```
解决办法：把figure.doc记事本放在F盘MATLAB的工作文件中即可

<font color="red">2.记事本中没办法插入表格，然后我就在记事本中把表格数据复制过去了，命名为t.txt,但是没办法用MATLAB命令得到t.txt中的数据</font>

``` MATLAB
[name,type,x,y,answer]=textread('t.txt','%s Type%n %n %n %s',1) 
% [A,B,C,D...]=textread('filename','format',N),其中A,B,C,D是每一列数据所要保存的变量名，format为读取格式,N是读取几次

总是出错
```

| names | types |  x  |  y  | answers |
| :---: | :---: |:---:|:---:| :---: |
|  lili |  girl |  1  |  2  |  yes  |





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

未定义变量 "figure" 或类 "figure.doc".
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

3.将MATLAB中数据写入记事本中

``` MATLAB
% 将MATLAB中的数据保存为一个普通的.txt文件，任何软件都可以查看，使用fprintf函数
% 建立.txt文件
fip=fopen('tp.txt','wt'); %建立一个文件，返回一个指标
fprintf(fip,'This is the datebase of class1.\n'); %直接在文件中写入一句话，当然也可以不写
names='lili';types=1;x=2;y=3;answers='yes'; % 把数据赋值，赋值变量名与fprintf中的A1,,,An要一致
fprintf(fip,'%s Type%u %u %u %s\n',names,types,x,y,answers); %fprintf(fileID,formatSpec,A1,...,An)；%s是字符串；%f表示浮点数；%u表示十进制数，易错
fclose(fip) % 最后不要忘记关闭文件
```

记事本tp.txt中效果如下：

This is the datebase of class1.

lili Type1 2 3 yes

### 1.2 数据拟合方法

#### 1.2.1 多项式拟合

``` MATLAB
x=[1,2,3,4,5,6,7,8,9];
y=[1,2,9,16,21,35,48,64,81]; % 点的x,y坐标值
p = polyfit(x,y,2);% n是拟合的最高次幂,就是拟合得到的函数是2次的；p是返回的多项式系数
xi=0:0.2:10;% 拟合曲线的横坐标
yi=polyval(p,xi);% 拟合得到的纵坐标
plot(xi,yi,'g  ',x,y,'r *') % xi,yi是一条曲线，后边有该曲线相应的款式和颜色设置；x,y是另一条曲线，同理
```
![拟合图](https://chunliblog.oss-cn-beijing.aliyuncs.com/images/MATLAB%E6%88%AA%E5%9B%BE.png)


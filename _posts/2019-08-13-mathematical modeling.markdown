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

1.多项式拟合指令

``` MATLAB
x=[1,2,3,4,5,6,7,8,9];
y=[1,2,9,16,21,35,48,64,81]; % 点的x,y坐标值
p = polyfit(x,y,2);% n是拟合的最高次幂,就是拟合得到的函数是2次的；p是返回的多项式系数
xi=0:0.2:10;% 拟合曲线的横坐标
yi=polyval(p,xi);% 拟合得到的纵坐标
plot(xi,yi,'g  ',x,y,'r *') % xi,yi是一条曲线，后边有该曲线相应的款式和颜色设置；x,y是另一条曲线，同理
```
![拟合图](https://chunliblog.oss-cn-beijing.aliyuncs.com/images/MATLAB%E6%88%AA%E5%9B%BE.png)

2.图形窗口的多项式拟合

``` MATLAB
x=[1,2,3,4,5,6,7,8,9];
y=[1,2,9,16,21,35,48,64,81]; % 点的x,y坐标值
plot(x,y,'r *') 
```
可以直接描点画出点状图，然后点击图形框——工具——基本拟合——选择中心化并缩放数据，再选择几个模拟选项进行比较即可

#### 1.2.2 指定函数拟合

``` MATLAB
syms t %先设一个符号变量，用于进行函数的化简和计算,这里t不加括号
x=[0;0.4;1.2;2;2.8;3.6;4.4;5.2;6;7.2;8;9.2;10.4;11.6;12.4;13.6;14.4;15];
y=[1;0.85;0.29;-0.27;-0.53;-0.4;-0.12;0.17;0.28;0.15;-0.03;-0.15;-0.071;0.059;0.08;0.032;-0.015;-0.02];%点坐标
f=fittype('a*cos(k*t)*exp(w*t)','independent','t','coefficients',{'a','k','w'});%fittype是自定义拟合曲线，第一个是自定义式，第二个标明独立变量为t，第三部分标明参数a,k,w
cfun=fit(x,y,f)%fit是根据自定义的函数来拟合给出的数据点，显示拟合函数
xi=0:0.1:20;
yi=cfun(xi);
plot(x,y,'r *',xi,yi,'g -')
```
在命令行会显示拟合之后得到的参数及置信区间：

``` MATLAB
cfun = 

     General model:
     cfun(t) = a*cos(k*t)*exp(w*t)
     Coefficients (with 95% confidence bounds):
       a =      0.9987  (0.9836, 1.014)
       k =       1.001  (0.9958, 1.006)
       w =     -0.2066  (-0.2131, -0.2002)
```
拟合效果图：
![拟合效果图](https://chunliblog.oss-cn-beijing.aliyuncs.com/images/MATLAB2.png)

#### 1.2.3 曲线拟合工具箱

在命令行直接输入cftool,会出现相应的拟合框，如图：
![拟合框](https://chunliblog.oss-cn-beijing.aliyuncs.com/images/MATLAB3.png)
fitname:cfun;
然后设置一下x;y;Degree;
根据左下角的SEE、RMSE，表示方差越接近于0越好，R-squre越接近于1拟合效果越好；

### 1.3 数据拟合应用实例

#### 1.3.1 人口预测模型

1.描绘出人口分布散点图——初步确定拟合函数

图像非线性上升后趋于平稳，与下述函数走向比较接近

<div markdown="0">
<a href="https://www.codecogs.com/eqnedit.php?latex=y=\frac{1}{a&plus;b\times&space;e^{-t}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?y=\frac{1}{a&plus;b\times&space;e^{-t}}" title="y=\frac{1}{a+b\times e^{-t}}" /></a></div>

我们将非线性关系线性化，找到回归系数并进行拟合,<font color="red">但我不会算回归系数和F检验值</font>

``` MATLAB
clear
clc
% 读入人口数据（1971－2000年）
Y=[33815	33981	34004	34165	34212	34327	34344	34458	34498	34476	34483	34488	34513	34497	34511	34520	34507	34509	34521	34513	34515	34517	34519	34519	34521	34521	34523	34525	34525	34527]
% 读入时间变量数据（t＝年份－1970）
T=[1	2	3	4	5	6	7	8	9	10	11	12	13	14	15	16	17	18	19	20	21	22	23	24	25	26	27	28	29	30]
% 根据人口变化的点状图
% 线性化处理
for t = 1:30; 
   x(t)=exp(-t);
   y(t)=1/Y(t); % x,y也是一个矩阵
end
% 计算，并输出回归系数B
c=zeros(30,1)+1; % c是一个30行1列的全1矩阵，但我并不明白为什么要这样写？
X=[c,x']; 
B=inv(X'*X)*X'*y' % y=a+b*x，a=B(1,1),b=B(2,1)
for i=1:30, % 回归拟合值，误差，离差每个点都要算
% 计算回归拟合值    
    z(i)=B(1,1)+B(2,1)*x(i);
% 计算离差
    s(i)=y(i)-sum(y)/30;
% 计算误差    
    w(i)=z(i)-y(i);
end
% 计算离差平方和S
S=s*s';
% 回归误差平方和Q
Q=w*w';
% 计算回归平方和U
U=S-Q;
% 计算，并输出F检验值，什么叫F检验值？
F=28*U/Q
% 计算非线性回归模型的拟合值
for j=1:30,
    G(j)=1/(B(1,1)+B(2,1)*exp(-j));
end
% 输出非线性回归模型的拟合曲线（Logisic曲线）
plot(T,G,T,Y,'g *')
```
![非线性-线性回归拟合结果](https://chunliblog.oss-cn-beijing.aliyuncs.com/images/MATLAB/1-3-1-1.png)






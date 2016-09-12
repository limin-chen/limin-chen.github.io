---
layout: post
title: R plotting Scripts
cover: wide_cover.jpg
date:  2014-05-22 11:23:20
categories: posts
comments: true

---

## R plotting Scripts

*写这篇博客目的只是为了帮助更多的文科生开始学习使用一些R的程序进行声调测量，内容大多是对于程序编写的说明，原R代码以及数据sample上传至dropbox。如果有任何疑问和错误，大家可以指出，共同维护这个博客的继续运行。多谢诸位！^_^*

*感谢Zhang Ben在程序编写和统计知识上对于我的引导和帮助，希望大家尊重劳动成果，引用时需要注明出处。*

### 1. Line Plotting

一般画声调的曲线是会采用Line Plotting，以下介绍最为简单的部分，其他多图，复杂部分均为在此基础上的修改。

####数据的格式要求：

<style>
<!--table
	{mso-displayed-decimal-separator:"\.";
	mso-displayed-thousand-separator:"\,";}
@page
	{margin:1.0in .75in 1.0in .75in;
	mso-header-margin:.5in;
	mso-footer-margin:.5in;}
.style0
	{mso-number-format:General;
	text-align:general;
	vertical-align:bottom;
	white-space:nowrap;
	mso-rotate:0;
	mso-background-source:auto;
	mso-pattern:auto;
	color:black;
	font-size:12.0pt;
	font-weight:400;
	font-style:normal;
	text-decoration:none;
	font-family:Calibri, sans-serif;
	mso-font-charset:0;
	border:none;
	mso-protection:locked visible;
	mso-style-name:Normal;
	mso-style-id:0;}
td
	{mso-style-parent:style0;
	padding-top:1px;
	padding-right:1px;
	padding-left:1px;
	mso-ignore:padding;
	color:black;
	font-size:12.0pt;
	font-weight:400;
	font-style:normal;
	text-decoration:none;
	font-family:Calibri, sans-serif;
	mso-font-charset:0;
	mso-number-format:General;
	text-align:general;
	vertical-align:bottom;
	border:none;
	mso-background-source:auto;
	mso-pattern:auto;
	mso-protection:locked visible;
	white-space:nowrap;
	mso-rotate:0;}
.xl65
	{mso-style-parent:style0;
	text-align:center;
	border:.5pt solid windowtext;}
-->
</style>

<table border=0 cellpadding=0 cellspacing=0 width=423 style='border-collapse:
 collapse;table-layout:fixed;width:423pt'>
 <col width=38 style='mso-width-source:userset;mso-width-alt:1621;width:38pt'>
 <col width=35 span=11 style='mso-width-source:userset;mso-width-alt:1493;
 width:35pt'>
 <tr height=15 style='height:15.0pt'>
  <td height=15 class=xl65 width=38 style='height:15.0pt;width:38pt'>1a</td>
  <td class=xl65 width=35 style='border-left:none;width:35pt'>1.5</td>
  <td class=xl65 width=35 style='border-left:none;width:35pt'>1.38</td>
  <td class=xl65 width=35 style='border-left:none;width:35pt'>1.18</td>
  <td class=xl65 width=35 style='border-left:none;width:35pt'>0.95</td>
  <td class=xl65 width=35 style='border-left:none;width:35pt'>0.73</td>
  <td class=xl65 width=35 style='border-left:none;width:35pt'>0.52</td>
  <td class=xl65 width=35 style='border-left:none;width:35pt'>0.32</td>
  <td class=xl65 width=35 style='border-left:none;width:35pt'>0.14</td>
  <td class=xl65 width=35 style='border-left:none;width:35pt'>0</td>
  <td class=xl65 width=35 style='border-left:none;width:35pt'>-0.12</td>
  <td class=xl65 width=35 style='border-left:none;width:35pt'>-0.19</td>
 </tr>
 <tr height=15 style='height:15.0pt'>
  <td height=15 class=xl65 style='height:15.0pt;border-top:none'>1b</td>
  <td class=xl65 style='border-top:none;border-left:none'>-0.42</td>
  <td class=xl65 style='border-top:none;border-left:none'>-0.45</td>
  <td class=xl65 style='border-top:none;border-left:none'>-0.42</td>
  <td class=xl65 style='border-top:none;border-left:none'>-0.37</td>
  <td class=xl65 style='border-top:none;border-left:none'>-0.29</td>
  <td class=xl65 style='border-top:none;border-left:none'>-0.2</td>
  <td class=xl65 style='border-top:none;border-left:none'>-0.07</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.1</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.35</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.63</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.88</td>
 </tr>
 <tr height=15 style='height:15.0pt'>
  <td height=15 class=xl65 style='height:15.0pt;border-top:none'>2ab</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.29</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.36</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.45</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.51</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.51</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.45</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.33</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.13</td>
  <td class=xl65 style='border-top:none;border-left:none'>-0.18</td>
  <td class=xl65 style='border-top:none;border-left:none'>-0.57</td>
  <td class=xl65 style='border-top:none;border-left:none'>-1.04</td>
 </tr>
 <tr height=15 style='height:15.0pt'>
  <td height=15 class=xl65 style='height:15.0pt;border-top:none'>3a</td>
  <td class=xl65 style='border-top:none;border-left:none'>2.31</td>
  <td class=xl65 style='border-top:none;border-left:none'>2.25</td>
  <td class=xl65 style='border-top:none;border-left:none'>2.09</td>
  <td class=xl65 style='border-top:none;border-left:none'>1.84</td>
  <td class=xl65 style='border-top:none;border-left:none'>1.48</td>
  <td class=xl65 style='border-top:none;border-left:none'>1.07</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.62</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.16</td>
  <td class=xl65 style='border-top:none;border-left:none'>-0.31</td>
  <td class=xl65 style='border-top:none;border-left:none'>-0.75</td>
  <td class=xl65 style='border-top:none;border-left:none'>-1.2</td>
 </tr>
 <tr height=15 style='height:15.0pt'>
  <td height=15 class=xl65 style='height:15.0pt;border-top:none'>3b</td>
  <td class=xl65 style='border-top:none;border-left:none'>-0.14</td>
  <td class=xl65 style='border-top:none;border-left:none'>-0.21</td>
  <td class=xl65 style='border-top:none;border-left:none'>-0.38</td>
  <td class=xl65 style='border-top:none;border-left:none'>-0.61</td>
  <td class=xl65 style='border-top:none;border-left:none'>-0.88</td>
  <td class=xl65 style='border-top:none;border-left:none'>-1.17</td>
  <td class=xl65 style='border-top:none;border-left:none'>-1.47</td>
  <td class=xl65 style='border-top:none;border-left:none'>-1.77</td>
  <td class=xl65 style='border-top:none;border-left:none'>-2.07</td>
  <td class=xl65 style='border-top:none;border-left:none'>-2.37</td>
  <td class=xl65 style='border-top:none;border-left:none'>-2.68</td>
 </tr>
 <tr height=15 style='height:15.0pt'>
  <td height=15 class=xl65 style='height:15.0pt;border-top:none'>1a</td>
  <td class=xl65 style='border-top:none;border-left:none'>0</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.13</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.27</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.4</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.54</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.67</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.81</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.94</td>
  <td class=xl65 style='border-top:none;border-left:none'>1.08</td>
  <td class=xl65 style='border-top:none;border-left:none'>1.21</td>
  <td class=xl65 style='border-top:none;border-left:none'>1.35</td>
 </tr>
 <tr height=15 style='height:15.0pt'>
  <td height=15 class=xl65 style='height:15.0pt;border-top:none'>1b</td>
  <td class=xl65 style='border-top:none;border-left:none'>0</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.14</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.28</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.41</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.55</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.69</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.83</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.96</td>
  <td class=xl65 style='border-top:none;border-left:none'>1.1</td>
  <td class=xl65 style='border-top:none;border-left:none'>1.24</td>
  <td class=xl65 style='border-top:none;border-left:none'>1.38</td>
 </tr>
 <tr height=15 style='height:15.0pt'>
  <td height=15 class=xl65 style='height:15.0pt;border-top:none'>2ab</td>
  <td class=xl65 style='border-top:none;border-left:none'>0</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.12</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.23</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.35</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.46</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.58</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.7</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.81</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.93</td>
  <td class=xl65 style='border-top:none;border-left:none'>1.04</td>
  <td class=xl65 style='border-top:none;border-left:none'>1.16</td>
 </tr>
 <tr height=15 style='height:15.0pt'>
  <td height=15 class=xl65 style='height:15.0pt;border-top:none'>3a</td>
  <td class=xl65 style='border-top:none;border-left:none'>0</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.08</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.16</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.24</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.32</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.4</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.47</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.55</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.63</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.71</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.79</td>
 </tr>
 <tr height=15 style='height:15.0pt'>
  <td height=15 class=xl65 style='height:15.0pt;border-top:none'>3b</td>
  <td class=xl65 style='border-top:none;border-left:none'>0</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.11</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.23</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.34</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.45</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.57</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.68</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.79</td>
  <td class=xl65 style='border-top:none;border-left:none'>0.91</td>
  <td class=xl65 style='border-top:none;border-left:none'>1.02</td>
  <td class=xl65 style='border-top:none;border-left:none'>1.13</td>
 </tr>
</table>


  
  
  **需要注意的地方有两点：**
  
   *此处还是请参加照dropbox中文件的样式，有bug，暂时还没debug。*
  
  1.表格第一列第一行空格中为Title，可以修改，例如画发音人T1，可将“Tone system”修改为“Speaker T1”.
  
  2.一定要保持声调列一一对应。上面为pitch值或归一化后的pitch值，下面为时长或归一化后的时长。 


----
####现在是R script 部分：
** 用紫色区块标出来的均为代码部分。**

首先，要现在R里导入我们读取数据、调整数据、以及画图的库。

`library(xlsx)`
read the data from excel file .xlsx

`library(reshape)`
melt the data

`library(ggplot2)`
plotting the pitch contour
  
`data <- read.xlsx("test.xlsx", sheetIndex = 1, encoding = "UTF-8", header = F)` Read data from excel 

`title <- toString(data[1,1])` 命名标题

`data$X1 <- NULL` 将第一列的值定义为空。

`separateLine <- which(data$X2 == data$X2[1])[2]` 寻找pitch值和duration值的分界行。

`ydata <- melt(data[1:(separateLine-1),],  id = c("X2"))` 将pitch部分data读取，定义为ydata

`xdata <- melt(data[separateLine:nrow(data),],  id = c("X2"))`将duration部分的data读取，义为xdata

`alldata <- cbind(xdata, ydata)`合并两个data

`colnames(alldata) <- c("tone", "", "x", "", "", "y")` 对列进行命名

`f1 <- ggplot(alldata, aes(x = x, y = y, colour = tone, shape = tone)) + `
       读取数值，画图。
       
  `geom_line(size=1.2) +`控制线的宽度
   
  `geom_point(size=3) +`控制点的大小
   
  `theme_bw() +` 
   默认背景为灰色，这行可换成白底
   
  `scale_shape_manual(values=1:11) + `
  
  
  `xlab("Duration(ms)")+`
   对X轴命名
  
  `ylab("Log z-score F0(Hz)")+`
   对y轴命名
  
  `ggtitle(paste("Puxian Min", title))`
   整个图片命名
   
 --- 
#### 根据上面出来的效果图：
![Alt text]({{ site.url }}/images/plot.png)


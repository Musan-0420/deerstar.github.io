---
title: 在vivado里初始化memory和数组
date: 2019-04-23 16:51:06
tags: FPGA，vivado， 数组
categories: 
  - FPGA
  - 基础  
toc: true
---

方法1：
将文件存为.mem格式，然后将它们添加到vivado项目中。
您可以像使用`"Add Sources"`然后选择 "Files of type: Memory Initialization Files".  
Vivado会自动将它们识别为内存文件.  
![vivado工程mem文件](image/screenshot/2019-04-23-21-08-25.png)  
Initialize Memory in Verilog — Time to Explore
https://timetoexplore.net/blog/initialize-memory-in-verilog 


方法2：
用initial语句进行初始化  
ug627里的官方说明，为将仿真和综合区别开，请标明索引  
![gu627](image/screenshot/2019-04-23-22-32-11.png)  
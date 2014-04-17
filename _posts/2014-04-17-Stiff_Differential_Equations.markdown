---
layout: post
title: Stiff Diferential Equations
author: copied from internet
abstract: 关于常微分方程中“刚性”概念的介绍
categories: 
 - 科学
tags: 
 - 常微分方程
 - ordinary differential equations
 - 刚性
 - stiffness
 - 解算器
date: 2014-04-17 13:00:00
---

## 0 引言

在做SIMULINK仿真时，有很多解算器（solver）可以使用，比如：

    * ode45     4阶5阶Runge-Kutta法。采用4阶方法提供候选解，5阶方法控制误差[1]。
    * ode23
    * ode113
    * ode15s
    * ode23s
    * ode23t
    * ode23tb

这些解算器分为两类——“刚性”（stiff）和“非刚性”（nonstiff）的。

## 1 刚性

“刚性”并不是指实际系统的物理特性，而是在对连续系统做仿真时遇到的一个数值问题。“刚
性”可以简单的认为是模型固有的在几个数量级之间变化的时间常数\[2\]。不同的算法具有
各自的稳定区域。刚性微分方程最好用刚性结算器求解，反之依然。

目前没有什么标准的方法区分刚性和非刚性系统。从现象上判断，如果用错了解算器会导致
仿真速度变慢，或者仿真结果不正确。如果无法确定系统该用哪种解算器，那就不妨都试一
试，比较一下结果和仿真速度，再来确定使用哪个解算器。

另外，mathworks给出了如何选用解算器的建议\[3\]。

    解算器  类型        准确度  适用场合

    ode45   非刚性      中      大多数场合。没别的特殊要求的话，就用这个解算器。

    ode23   非刚性      低      适用于对精度要求不高或者部分刚性的问题。

    ode113  非刚性      低到高  适用于有严格精度要求或计算量很大的问题。
    
    ode15s  刚性        低到中  相当于刚性版的“ode45”。

    ode23s  刚性        低      适用于对精度要求不高，或质量矩阵是常数的问题。

    ode23t  部分刚性    低      适用于部分刚性并要求解中不含numerical damping的问题。
    
    ode23tb 刚性        低      适用于精度要求不高的刚性问题。

## 关于刚性的扩展阅读：

[Stiff Differential Equations By Cleve Moler](http://www.mathworks.cn/company/newsletters/articles/stiff-differential-equations.html)

[Stiff systems](www.scholarpedia.org/article/Stiff_systems)

## 参考文献

\[1\] [百度百科-ode45](http://baike.baidu.com/link?url=i56H2pPWMUbNdtccBa2rAazWA27Neze3loXNd_JdA6aZbMYn0j-MYVmAewFq5hdkHEEgKO_xGpayTC1wl_ZqjK)

\[2\] [www.plexim.com/suppport/solutions/158](www.plexim.com/suppport/solutions/158)

\[3\] [http://www.mathworks.cn/cn/help/matlab/ref/ode45.html](http://www.mathworks.cn/cn/help/matlab/ref/ode45.html)

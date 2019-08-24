---
layout: post
title: ACM训练第17天
date: 2019-8-15
categories: blog
tags: [算法,数学,训练]
description: 语言
---

### behind
今天B组总结一下。第一题骰子问题，二点可能斜着可能竖着，因为这道题默认是斜着，所以错了一发，但是比赛完了去搜了一下，题目没有说清楚，本来就有两种情况。第二题暴力会TLE这是一定的，但是题目后面的hint说坐标在10的18次方，这是什么鬼，题面上面才说是5000，但比赛后看了一下，用bfs预处理了一下（居然不会超时，样例都要跑2秒多）。第三道题博弈，题面很难，目测暴力，但有人10几行代码A了，这不得不说是规律博弈题，想了半天，最后奇偶数大法A了这道题，H题以为能做出来，但是思路都没有，比赛后看了看，异或博弈，还没学。。。。。，做题还是缺乏定力，。

### 今日份get--数学 拓展欧几里得算法
入门精讲：<https://www.luogu.org/blog/user55458/tong-yu-fang-cheng><br/>
拓展欧几里得讲解：<https://www.cnblogs.com/yuelingzhi/archive/2011/08/13/2137582.html><br/>



## 题目（部分）

###  Security Guards 
题目链接：<https://vjudge.net/contest/313279#problem/B><br/>
先把所以保安的位置在5000* 5000的图上用bfs向8个方向拓展，记录最小步数，最后直接用坐标查询即可。<br/>

### A - Romantic 
题目链接:<https://vjudge.net/contest/319143#problem/A><br/>
拓展欧几里得板子题，大意输入a,b,输出满足a * x + b * y = 1;的非负整数x和整数y。这道题提交了多次，就是因为关闭了cin,cout的同步流，以后记住不能随便关这个<br/>


### 青蛙的约会 poj 1061
题目链接：<https://vjudge.net/contest/313337#problem/B><br/>
讲解：<https://blog.csdn.net/weixin_43916296/article/details/86379197 ><br/>
拓展欧几里得衍生题，根据题意得出大概像a * x + y * b = C的样子，对后面是一个整数，不着急上面有讲解好好研究研究<br/>

![哪吒](/img/lz3.jpg)










---
layout: post
title: ACM训练第23天（计算几何）
date: 2019-8-21
categories: blog
tags: [算法,训练,计算几何]
description: 语言
---

### 写在前面
今天是我的锅，两道题因为想错了算法而止步不前，唉，把floyld求闭包想成了并查集，awsl，真的，今天有点怄气，题做不动，还把船聊没了（私事）。计算几何杀我，可能还是菜鸡，初次接触此类题，大眼瞪小眼，涉及了计算几何方面的题，所以不知道也是正常，慢慢来嘛，不能步，怎能run。

### 题目
今天呢，题目涉及foyld算法求闭包，dp动态规划递推求解，另外就是杀我的计算几何之叉积求点与线段之间的关系。<br/>



### Problem D Pants On Fire floyld算法求闭包
题目链接：<https://codeforces.com/gym/101873/attachments/download/7413/20172018-acmicpc-german-collegiate-programming-contest-gcpc-2017-en.pdf><br/>
知道题目算法的我眼泪掉下来，并查集写了一发，以wa test 3结尾，这个就在告诉你算法不对头，实际上我们都商量出来算法问题，但苦于不知道上面算法而告终，事后自敲一发传递闭包
AC。


### Problem I Überwatch dp动态规划递推
题目链接：<https://codeforces.com/gym/101873/attachments><br/>
做的时候队友一直建议深搜写，实际上这是不可能的，超时是最大的障碍，300000的数据，深搜是不可能了，这时又没有好的算法策略而停滞不前，事后（又是事后。。。），知道dp后，用我们原来深搜的思想推出了dp的状态转移方程，一发失败，因为第一次是m+1那个点开始，第二发AC。



### A - TOYS 计算几何---二分+叉积
题目链接：<https://vjudge.net/contest/321263#problem/A><br/>
涉及计算几何关于线段与点位置关系的基础知识。看链接快速了解。<br/>
点与直线的位置关系，传送门：<https://blog.csdn.net/qiushangren/article/details/90475707><br/>
向量积居然能怎么用，我是长知识了。<br/>


### B - Toy Storage 同上面一道题
题目链接：<https://vjudge.net/contest/321263#problem/B><br/>
和上面一道题叙述完全一样，只不过输入不再是有顺序的隔板坐标，而是无序的，需要你重新排序，我觉得我的stl用的还是挺巧妙地（哈哈哈哈哈哈哈哈哈哈）。








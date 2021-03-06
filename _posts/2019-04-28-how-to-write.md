---
layout: post
title: 快读大法
date: 2019-4-28
categories: blog
tags: [算法,模拟]
description: 语言
---

## 先从例题引入

## 改良计算器

### 题目背景
>NCL是一家专门从事计算器改良与升级的实验室，最近该实验室收到了某公司所委托的一个任务：需要在该公司某型号的计算器上加上解一元一次方程的功能。实验室将这个任务交给了一个刚进入的新手ZL先生。

### 题目描述
>为了很好的完成这个任务，ZL先生首先研究了一些一元一次方程的实例：<br/>
>>4+3x=8<br/>

>>6a−5+1=2−2a<br/>

>>−5+12y=0<br/>

>>ZL先生被主管告之，在计算器上键入的一个一元一次方程中，只包含整数、小写字母及+、-、=这三个数学符号（当然，符号“-”既可作减号，也可作负号）。方程中并没有括号，也没有除号，方程中的字母表示未知数。<br/>

>>你可假设对键入的方程的正确性的判断是由另一个程序员在做，或者说可认为键入的一元一次方程均为合法的，且有唯一实数解。<br/>

### 输入输出格式
#### 输入格式
>一个一元一次方程。
#### 输出格式
>解方程的结果(精确至小数点后三位)。

### 输入输出样例
>输入样例
>>6a-5+1=2-2a<br/>
>输出样例
>>a=0.750<br>

经过~~反复~~的思考，大致有一个思路，只不过很麻烦，就是：<br/>
1. 题目是解一元二次方程，最后的结果肯定是未知数的系数除以常数和。
2. 把等式分为两部分，等号两边。
3. 分别求解常数和，和未知数系数和。
4. 最后求解。

那么问题来了，输入肯定是字符串，而且不知道长度，后面读字符串的话，肯定要转化为数字，这样做需要大量的判断<br/>
比如：如果你找到了未知数的位置，你将要判断它前面的数字，有数字，你还要判断前面的前面个数字，如果是符好，你还要判断是证号还是负号，而且如果未知数是第一个位置上的话，系数就为1.....<br/>

这尚且是第一个：未知数的判断方法，还有常数，而且还是等号一边？？？！！！！！<br/>

可见工程量绝对不小，所以**快读大法**应运而生(bgm--大河向东流)<br/>

所谓快读也叫做边写边读，类似getchar(),scanf("%c",&c),这种，未知长度，那我就一个一个读，并且模拟解题过程。<br/>
**需要注意的是，需要将未知数和常数移到不同的两边**

    #include <bits/stdc++.h>
    using namespace std;
    int cs=0,xs=0;//分别代表常数系数和，和未知数系数和
    int fh1=1,fh2=1;//分别代表前面的符号
    int sum=0;//把字符转换为一个数字
    char ch;//记录未知数
    int main()
    char c;
    while(~scanf("%c",&c))//开始一个一个输入，
     {
       if(c>='0'&&c<='9')//判断是否为数字
       {
          sum=(sum*10+(c-'0'))*fh1*fh2;//字符转换为数字
       }
       else
       {
           if(c>='a'&&c<='z')//找到未知数
           {
               ch=c;//记录
              if(sum==0)//前面没有系数
              {
                  xs+=fh1*fh2;//为1或-1（1取决于前面的符号）
              }
              else
              {
                  xs+=sum;//有系数，赋值
              }
           }
           else
            cs+=sum;//常数赋值
           sum=0;//重新清零
       }
       if(c=='+')
         {fh1=1;continue;}//判断符号
       if(c=='-')
        {fh1=-1;continue;}
       if(c=='=')
        {
            fh2=-1;
            fh1=1;
            continue;
        }
        }
     float a=(float)cs/xs;
     printf("%c=%.3f",ch,a==0?0.000:a*(-1));//输出有个坑
    cout<<cs<<" "<<xs;
    }

**在c++中，当转换为浮点数后，会有-1/0=-0的情况出现，所以这时候就要判断**这个需要注意<br/>
代码是这样写，但我有个bug调了一个小时（哭辽），就是化为数字那里，~~太菜了~~，多打多练，很重要啊！！！








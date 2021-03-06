---
layout: post
title: 倒水
date: 2019-7-8
categories: blog
tags: [算法,暴力优先搜索,uva]
description: 语言
---
### 写在前面
  在写这道题之前，我先说说最近发生的事情。<br/>
  上周末考完c++了，虽然开始做着有点紧张，但还是慢慢滴进入了状态，越做越顺手，只不过都是语法题，也谈不上难，但最后一道柠檬还是把我酸了，哈哈哈，看来我还修行不够啊。。。。<br/>
就在考完的第二天，你会看到很多西装革履的人，他们匆匆忙忙去参加部门的部长选拔。很多人问我，问什么你一个部门都不留呢，我的回答也是模模糊糊。说实话，我就是有点不喜欢有东西支配我的时间，我想做一些自己想做的事情，最后我也回了他们一句我的心声，我想下学期有更多可能性。但今天他们结果下来了，我也替他们被选上而高兴，但莫名其妙的心情忽然失落了一段时间。我在想我是不是错过了一些东西，看见他们有东西可以忙，而我的下学期像我说的一样，充满可能性，都是未知数，可能我怕像有些学长一样，与更多的时间不是充实自己，而是疯玩。但后来，我也在想，我自己做的决定，我会对它负责到底，而不是怀疑自己，各有各自的好处，这个我不加评判，想得到一些东西，那就肯定得失去些什么，下学期我将会去寻找我真正想做的事，加油，真正的让下学期充满可能性，冲冲冲!!!!!<br/>
  实际上这也到了，分别的时刻了，实际上也是不见不散吧，但是不能在一起工作了而已，我总是说，上学期太累了，总是瞎忙，但现在回头看看，并非如此，收获了很多东西，只不过，那些东西会像酒一样，会随着时间而更加醇香！<br/>
### 开始正题
## UVA10603 倒水问题
### 题目大意
设3个杯子的容量为abc，起初只有第三个杯子装满了c升水。其它两个杯子均为空。最少要倒多少升水可以让某一个杯子里有d升水。如果无法做到d升水。就让某个杯子里有d‘升水，其中d’< d而且尽量接近d（1<=a,b,c,d<=200）要求输出最小的倒水量和目标水量（d或者是d‘）<br/>
### 题目理解
作为一道紫书上的列题，出现在隐式图的暴力搜索上面，它连接了图论与搜索，首先这道题有个难点就是建模，建立一个有向图，把每个状态作为结点（谈到状态，虽然我初次接触，但很多大佬都说它玄学，lrj说状态在很多算法中很重要，行扒，记着了！），之后把最少倒水量作为两两结点的权值，这就形成了一个有向图，还有就是谈到最小值，要想到bfs,因为广搜用于最小值很管用，反正我还没有体会到，菜鸡的我还只知道，DFS递归代码少但维护很难，BFS某种意义上来说确实很好，这个在以后做题在慢慢发掘吧。还有一个关键就是这里用到了Dijkstra算法，初次接触这个算法，还是在离散数学课堂上，这个算法简单来说，就是把BFS的点的拓展限制一下，原来BFS是要每个点都拓展，Dijkstra偏不，就从倒水量最少的点拓展，这就是这道题的精华之处。再谈谈体会：
首先是进行枚举操作的时候，虽然总共三个杯子，作者还是把数据放到了数组里面，简化不少代码，如果是我的话，就直接写9个if了。

然后是代码的思想是 dijkstra，求最短路。

把整个问题当做一个状态图，每个点由三个水杯里面的水确定。
两个点之间的边的权值，是由两个状态转化所需要转移的水量。（注意一点是这里是有向图）
另外三个水杯里面的水合不变，给定两个水杯里水的体积，就可以确定另一个，所以储存状态时，只需要记录两个水杯的体积即可。
经过上面的解析，这个问题就抽象成了，求一个有向图的最短路径，然后使用了优先队列优化的 dijkstra 。

另外memcpy的使用值得一学，使用方法如下： 
memcpy(&a, &b, sizeof(b)); 
把 b 复制给a，直接复制的内存，效率比直接循环快。

1、vis数组只用开两维

看到讨论中大家都是用的三维数组vis[201][201][201]，其实有了两杯水的数据，第三杯水可以用总量减去两杯水的量得到，所以不需要维护3维数组

2、解的存储

因为题目说如果取不到d，就要打印出比d小的最大的可能解d'以及倒水的量，所以bfs就把所有可能的d以及倒水量都存了下来，如果之前取到过这个d，则判断倒水量是否比之前的少，如果满足要求的话就更新数据。最后从d开始往下减小，遇到第一个取到过的解就打印并返回

3、优先队列

首先要注意这道题问的是倒水量最少，而不是倒水次数最少，而这两者没有必然关系。所以在bfs的时候，就不能用普通queue存储需要遍历的节点，而应该用一个优先队列，让倒水量少的排在前头。

另外在讨论中看到很多人用的是dfs，并且很多人得了TLE。然后大家比较推荐的解法是dijkstra。

<p style="color: red;">lrj说在学完Dijkstra算法之后还有其他体会，行！我以后再来补充一波</p>

### input
2

2 3 4 2

96 97 199 62
### output
2 2

9859 62

### AC代码

    #include <bits/stdc++.h>
    using namespace std;
    typedef struct node
    {
    int v[3];
    int dis;
    bool operator<(const node &a)const//给优先队列加上判断条件
    {
      return dis>a.dis;
     }
    }node;
    const int maxn=200+10;
    int ans[maxn],vis[maxn][maxn],cap[4];//cap数组装入三个杯子的体积
     int update_ans(const node a)//ans数组判断是否达到那个水量，vis判断每个状态（杯子剩余水量）
    {//更新每个水量时的到水量
    for(int i=0;i<3;i++)
    {
        int b=a.v[i];
        if(ans[b]<0||ans[b]>a.dis)
        {
            ans[b]=a.dis;
        }
    }
    return 0;
    }
    void solve(int a,int b,int c,int d)
     {
    cap[0]=a,cap[1]=b,cap[2]=c;
    memset(ans,-1,sizeof(ans));
    memset(vis,0,sizeof(vis));
    node v1;
    v1.dis=0;
    v1.v[0]=0;v1.v[1]=0;v1.v[2]=c;
    priority_queue<node> s;//优先队列
    s.push(v1);
    vis[0][0]=1;
    while(!s.empty())
    {
        node a=s.top();s.pop();
        update_ans(a);
        if(ans[d]>=0)
        break;
        for(int i=0;i<3;i++)
        {
            for(int j=0;j<3;j++)
                if(i!=j)
            {
                if(a.v[i]==0||cap[j]==a.v[j])
                    continue;
                int count1=min(cap[j],a.v[i]+a.v[j])-a.v[j];//防止溢出
                node aa;
                memcpy(&aa,&a,sizeof(a));//内存拷贝
                aa.dis=a.dis+count1;
                aa.v[i]=a.v[i]-count1;
                aa.v[j]=a.v[j]+count1;
                if(!vis[aa.v[0]][aa.v[1]])
                {
                    s.push(aa);//插入队列
                    vis[aa.v[0]][aa.v[1]]=1;
                }
            }
        }
    }
    while(d>=0)
    {
        if(ans[d]>=0)
        {
            cout<<ans[d]<<" "<<d<<endl;
            return;
        }
        d--;
    }//寻找最小倒水量
    }
    int main()
    {
    int a,b,c,d;
    int n;
    cin>>n;
    while(n--)
     {
      cin>>a>>b>>c>>d;
      solve(a,b,c,d);
     }
    }











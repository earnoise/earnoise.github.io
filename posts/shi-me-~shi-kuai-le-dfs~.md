---
title: '什么～是快乐dfs～'
date: 2023-02-26 10:23:51
tags: [c++]
published: true
hideInList: false
feature: 
isTop: false
---
相信各位在洛谷刷题的时候，肯定会见到一个东西：
```cpp
void dfs(){
    // 懒得写(￣∇￣)
}
```
那这到底是个什么寄吧东西呢？
来，先看百度：
>深度优先搜索是一种在开发爬虫早期使用较多的方法。它的目的是要达到被搜索结构的叶结点(即那些不包含任何超链的HTML文件) 。在一个HTML文件中，当一个超链被选择后，被链接的HTML文件将执行深度优先搜索，即在搜索其余的超链结果之前必须先完整地搜索单独的一条链。深度优先搜索沿着HTML文件上的超链走到不能再深入为止，然后返回到某一个HTML文件，再继续选择该HTML文件中的其他超链。当不再有其他超链可选择时，说明搜索已经结束。

人话：
><h1>递推</h1>

辣么，我们拿道题来看看：
[洛谷P1644](https://www.luogu.com.cn/problem/P1644)
先上完整AC代码：
```cpp
#include<bits/stdc++.h>
using namespace std;
int m,n,t;
void dfs(int a,int b){
    if (a<0 || a>n || b>m) return;
    if (a==n && b==m){
        t++;
    }else{
        dfs(a+1,b+2);
        dfs(a+2,b+1);
        dfs(a-2,b+1);
        dfs(a-1,b+2);
    }
}
int main(){
    cin>>n>>m;
    dfs(0,0);
    cout<<t;
    return 0;
}
```
AC图片：
![](https://blog-yile.github.io/post-images/1677378679185.png)

来，逐条分析:
```cpp
void dfs(int a,int b){ // 上文讲到的Dfs
    if (a<0 || a>n || b>m) return; // 如果超出界限，或者必定无法到达(n, m)(超过)返回主程序
    if (a==n && b==m){ // 到达(n, m)则计数+=1
        t++;
    }else{ // 枚举
        dfs(a+1,b+2);
        dfs(a+2,b+1);
        dfs(a-2,b+1);
        dfs(a-1,b+2);
    }
}
```
想必int main()不用说了吧？
如果康不懂，建议重读呢亲亲。

byebye，摸鱼去啦。
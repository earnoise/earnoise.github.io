---
title: '欧拉筛(欧拉：为什么让我筛🤔'
date: 2023-02-27 10:00:00
tags: [c++]
published: true
hideInList: false
feature: 
isTop: false
---

先上代码：
```cpp
const int N=1e5+10;
int vis[N];    //0表示素数，1表示非素数
int prime[N];    //只在这个函数有作用
void Euler_prime()  //欧拉筛法
{
    for(int i=2;i<=N;i++)
    {
        if(!vis[i]) prime[x++]=i;
        for(int j=0;j<x;j++)
        {
            if(i*prime[j]>N) break;
            vis[i*prime[j]]=1;
            if(i%prime[j]==0) break;
        }
    }
}
```
思路：
为了实现让合数分解为——最小质因数 * 剩下的形式，我们将内层循环换为从最小的素数遍历到最大的素数，并且新增一条break语句，使得每次都以prime[j] * i的方式筛掉合数，如此就可以使得prime[j]为该合数的最小质因数。证明如下，改内层循环：prime是从最小遍历到最大的，且i使外层循环，总是大于prime的数字，所以prime[j] < i。加break语句：如果i =k * prime[j]，那么i * prime[j + 1] = prime[j] * k * prime[j + 1]显然此时prime[j + 1]不是该合数i * prime[j + 1]中的最小质因数，那么就说明该合数已经(之后)会被prime[j] 或者k中的最小质因数筛掉。即避免了重复筛选。

摆烂吧～
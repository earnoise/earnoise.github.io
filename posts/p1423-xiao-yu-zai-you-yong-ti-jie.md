---
title: 'P1423 小玉在游泳 题解'
date: 2023-03-03 15:12:47
tags: []
published: true
hideInList: false
feature: 
isTop: false
---
数学方法
O(1)时间复杂度
等比数列求和公式:
$$S_n=(a_1(1-q^n))/(1-q)(q{=}\mathllap{/\,}1)$$
每次游的距离为上一次的0.98倍，构成一个公比为0.98的等比数列
现要使其前ans项大于等于一个值
只要代入公式并向上取整即可
下附超短代码

源代码
```cpp
#include<bits/stdc++.h>
using namespace std;
double x;
int main()
{
    cin>>x;
    cout<<ceil(log(1-x/100)/log(0.98));
    return 0;
}
```

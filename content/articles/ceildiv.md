---
title: CeilDivision
description: 数学 切り上げ割り算
date: 2021/04/07
---

## 説明

## 計算量

## 実装例

```cpp
#include<bits/stdc++.h>
using namespace std;

template <typename T1,typename T2>
T1 ceilDiv(T1 a,T2 b){
  return (a+(b-1))/b;
}

int main(){
  int x,y;
  cin>>x>>y;
  cout<<ceilDiv(x,y)<<endl;
}
```

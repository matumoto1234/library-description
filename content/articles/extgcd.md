---
title: ExtendedGCD
description: 数学 拡張ユークリッドの互除法
date: 2021/04/07
---

## 説明

## 計算量

## 実装例

```cpp
#include<bits/stdc++.h>
using namespace std;

template <typename T>
T extgcd(T a,T b,T &x,T &y){
  if(b==0){
    x=1;
    y=0;
    return a;
  }
  T d=extgcd(b,a%b,y,x);
  y=y-(a/b)*x;
  return d;
}

int main(){
  long long a,b;
  cin>>a>>b;
  long long x,y;
  extgcd(a,b,x,y);
  cout<<x<<' '<<y<<endl;
}
```

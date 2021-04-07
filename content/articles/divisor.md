---
title: Divisor
description: 数学 約数列挙
date: 2021/04/07
---

## 説明

## 計算量

## 実装例

```cpp
#include<bits/stdc++.h>
using namespace std;

vector<long long> divisor(long long n){
  vector<long long> res;
  for(long long i=1;i*i<=n;i++){
    if(n%i==0){
      res.push_back(i);
      if(i*i!=n) res.push_back(n/i);
    }
  }
  sort(res.begin(),res.end());
  return res;
}

int main(){
  int n;
  cin>>n;
  vector<long long> v=divisor(n);
  for(int i=0;i<v.size();i++){
    cout<<v[i];
    cout<<(i==v.size()-1?"\n":" ");
  }
}
```

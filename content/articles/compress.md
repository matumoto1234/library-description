---
title: Compress
description: その他 座標圧縮
date: 2021/04/07
---

## 説明

## 計算量

## 実装例

```cpp
#include<bits/stdc++.h>
using namespace std;

vector<int> compress(vector<int> a){
  int n=a.size();
  vector<int> res=a;
  sort(a.begin(),a.end());
  map<int,int> mp;
  for(int i=0;i<n;i++){
    mp[a[i]]=i;
  }
  for(int i=0;i<n;i++){
    res[i]=mp[res[i]];
  }
  return res;
}

int main(){
  int n;
  cin>>n;
  vector<int> a(n);
  a=compress(a);
}
```
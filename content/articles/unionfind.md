---
title: UnionFind
description: データ構造 素集合データ構造
date: 2021/04/7
---

## 説明

## 計算量

## 実装例

```cpp
#include <bits/stdc++.h>
using namespace std;

struct UnionFind{
  int cnt;
  vector<int> siz,par;
  UnionFind(int N):cnt(N),siz(N,1),par(N){
    iota(par.begin(),par.end(),0);
  }

  int root(int x){
    if(x==par[x]) return x;
    return par[x]=root(par[x]);
  }

  int count(){ return cnt; }

  int size(int x){ return siz[root(x)]; }

  bool issame(int x,int y){ return root(x)==root(y); }

  void unite(int x,int y){
    x=root(x);
    y=root(y);
    if(x==y) return;
    if(siz[x]<siz[y]) swap(x,y);
    siz[x]+=siz[y];
    par[y]=x;
    cnt--;
  }
};
```

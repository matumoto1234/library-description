---
title: SmallestPrimeFactor
description: 数学 最小素因数分解
date: 2021/04/07
---

## 説明

## 計算量

## 実装例

```cpp
#include <bits/stdc++.h>
using namespace std;

// 1-indexed
class SmallestPrimeFactor {
public:
  SmallestPrimeFactor(int N):ps(N + 1,1){
    build();
  }

  vector<int> factorize(int x){
    vector<int> res;
    while(ps[x]!=1){
      res.push_back(ps[x]);
      x/=ps[x];
    }
    return res;
  }

  int operator[](int i) { return ps[i]; }

private:
  vector<int> ps;

  void build() {
    for (long long i = 2; i < ps.size(); i++) {
      if (ps[i] != 1) continue;
      ps[i] = i;
      for (long long j = i * i; j < ps.size(); j += i) {
        if (ps[j] != 1) continue;
        ps[j] = i;
      }
    }
  }
};
```
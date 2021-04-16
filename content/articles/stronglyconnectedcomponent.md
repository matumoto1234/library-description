---
title: StronglyConnectedComponent
description: グラフ 強連結成分分解
date: 2021/04/16
---

## 説明
強連結成分分解を行います

**強連結とは**  
二つの頂点間で互いに行き来できる

**強連結成分とは**  
集合に含まれる全ての頂点が互いに行き来できるような頂点集合

**アルゴリズム**  
1. どこかの頂点から深さ優先探索をして帰りがけ順に番号を振ります
2. グラフを逆辺にして番号が大きいものから深さ優先探索をします
3. 訪問した頂点が強連結成分に含まれます

## 計算量
$$
O(V+E)
$$

## 実装例

##### main関数内で解いている問題
> [https://onlinejudge.u-aizu.ac.jp/courses/library/5/GRL/3/GRL_3_C](https://onlinejudge.u-aizu.ac.jp/courses/library/5/GRL/3/GRL_3_C)

```cpp import=/assets/Library/graph/stronglyconnectedcomponent.cpp
```

## 参考
> [https://manabitimes.jp/math/125](https://manabitimes.jp/math/125)
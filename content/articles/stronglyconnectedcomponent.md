---
title: StronglyConnectedComponent
description: グラフ 強連結成分分解
date: 2021/04/07
---

## 説明
強連結成分分解を行います。

**強連結とは**  
二つの頂点間で互いに行き来できる

**強連結成分とは**  
集合に含まれる全ての頂点が互いに行き来できるような頂点集合

**流れ**  
1. どこかの頂点からDFSをして帰りがけ順に番号を振ります。
2. グラフを逆辺にして番号が大きいものからDFSをします。
3. 訪問した頂点が強連結成分に含まれます。

## 計算量
$$
O(V+E)
$$

## 実装例

```cpp import=/assets/Library/graph/stronglyconnectedcomponent.cpp
```

## 参考
> [https://manabitimes.jp/math/125](https://manabitimes.jp/math/125)
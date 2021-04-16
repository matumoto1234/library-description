---
title: ShortestHamiltonianPath
description: グラフ 最短ハミルトン経路
date: 2021/04/16
---

## 説明
最短ハミルトン経路のコストを求めます

**最短ハミルトン経路とは**  
全ての頂点を一度だけ訪問するような経路を指します

bit列によって訪問したかどうかを管理します

## 計算量
$$
O(V2^V)
$$

## 実装例

```cpp import=/assets/Library/graph/shortesthamiltonianpath.cpp
```

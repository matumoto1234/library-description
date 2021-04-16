---
title: ShortestHamiltonianCycle
description: グラフ 最短ハミルトン閉路
date: 2021/04/16
---

## 説明
最短ハミルトン閉路のコストを求めます

**最短ハミルトン閉路とは**  
全ての頂点を一度だけ訪問し始点に戻ってくるような閉路のことを指します

bit列によって訪問したかどうかを管理します

## 計算量
$$
O(V2^{V})
$$

## 実装例

```cpp import=/assets/Library/graph/shortesthamiltoniancycle.cpp
```

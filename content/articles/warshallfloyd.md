---
title: WarshallFloyd
description: グラフ 全点対間最短経路
date: 2021/04/06
---

## 説明
全点対間最短経路を求めます。負の閉路があれば左斜めの対角成分を見ることで検知できます。

**流れ**  
1. 隣接行列でグラフを管理する。
2. 頂点kを経由して頂点iから頂点jに向かったときのコストと頂点iから頂点jへのコストを比較する。


## 計算量
$$
O(V^{3})
$$

## 実装例

```cpp import=/assets/Library/graph/warshallfloyd.cpp
```

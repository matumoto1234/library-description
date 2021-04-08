---
title: Dijkstra
description: グラフ 単一始点最短経路
date: 2021/04/06
---

## 説明
単一始点最短経路を求めるアルゴリズムです。負の辺があっても負の閉路がなければ正しく動作します。  


## 計算量
頂点数をV,辺の数をEとすると
$$
O(ElogV)
$$

## 実装例
main関数内では[AOJ_GRL_1_A](https://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=GRL_1_A&lang=ja)を解いています。

```cpp import=/assets/Library/graph/dijkstra.cpp
```

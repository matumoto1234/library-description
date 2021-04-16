---
title: WarshallFloyd
description: グラフ 全点対間最短経路
date: 2021/04/16
---

## 説明
全点対間最短経路を求めます  
負の閉路があれば左斜めの対角成分を見ることで検知できます

**アルゴリズム**  
1. 隣接行列でグラフを管理する
2. 頂点$k$を経由して頂点$i$から頂点$j$に向かったときのコストと頂点$i$から頂点$j$へのコストを比較して更新する

## 計算量
$$
O(V^{3})
$$

## 実装例

##### main関数内で解いている問題
> [https://onlinejudge.u-aizu.ac.jp/courses/library/5/GRL/1/GRL_1_C](https://onlinejudge.u-aizu.ac.jp/courses/library/5/GRL/1/GRL_1_C)

```cpp import=/assets/Library/graph/warshallfloyd.cpp
```

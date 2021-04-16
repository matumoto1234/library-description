---
title: WeightedUnionFind
description: グラフ 重み付き素集合データ構造
date: 2021/04/16
---

## 説明
重みの付いた集合を管理します

**できること**  
- $2$つの集合を$1$つのグループにする
- $2$つの要素が同じ集合か判定する
- 同じ集合内で差分を管理する

<br>

**どのように差分を管理するのか**  
集合内の根を基準として, 根よりいくつ大きいか小さいかで同じ集合内での差分が求まります

## 計算量
$$
O(\alpha(N))
$$
$\alpha(N)$はアッカーマン関数の逆関数です

## 実装例

```cpp import=/assets/Library/data-structure/weightedunionfind.cpp
```

## 参考
> [https://onlinejudge.u-aizu.ac.jp/courses/library/3/DSL/1/DSL_1_](https://onlinejudge.u-aizu.ac.jp/courses/library/3/DSL/1/DSL_1_)
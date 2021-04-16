---
title: WeightedUnionFind
description: グラフ 重み付き素集合データ構造
date: 2021/04/08
---

## 説明
重みの付いた集合を管理します。

**できること**  
- 2つの集合を1つのグループにする。
- 2つの要素が同じ集合か判定する。
- 同じ集合内で差分を管理する。

**どのように差分を管理するのか**  
集合内の根を基準として、根よりいくつ大きいか小さいかで同じ集合内での差分が求まります。

## 計算量
$$
O(\alpha(N))
$$

## 実装例

```cpp import=/assets/Library/data-structure/weightedunionfind.cpp
```

## 参考
> [https://onlinejudge.u-aizu.ac.jp/courses/library/3/DSL/1/DSL_1_](https://onlinejudge.u-aizu.ac.jp/courses/library/3/DSL/1/DSL_1_)
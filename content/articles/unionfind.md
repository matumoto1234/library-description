---
title: UnionFind
description: データ構造 素集合データ構造
date: 2021/04/16
---

## 説明
集合を管理します

**できること**  
- $2$つの集合を$1$つのグループにする
- $2$つの要素が同じ集合か判定する

**考え方**  
- 集合を$1$つの木として考える
  - まとめる操作
  片方の根をもう片方の根にくっつける
  - 判定操作
  同じ根かどうかを判定する

**工夫**  
1. 経路圧縮  
  根を調べる際に辺を根に直接繋ぎ直す
2. ランク(もしくは集合の大きさ)  
  木の高さが低い方を高い方に繋げる

## 計算量
$$
O(\alpha(N))
$$
$\alpha(N)$はアッカーマン関数の逆関数です

## 実装例

```cpp import=/assets/Library/data-structure/unionfind.cpp
```

## 参考
> [https://atcoder.jp/contests/atc001/tasks/unionfind_](https://atcoder.jp/contests/atc001/tasks/unionfind_)
> [https://onlinejudge.u-aizu.ac.jp/courses/library/3/DSL/1/DSL_1_](https://onlinejudge.u-aizu.ac.jp/courses/library/3/DSL/1/DSL_1_)
> [https://rsk0315.hatenablog.com/entry/2020/11/14/17042](https://rsk0315.hatenablog.com/entry/2020/11/14/17042)
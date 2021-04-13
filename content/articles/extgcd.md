---
title: ExtendedEuclideanAlgorithm
description: 数学 拡張ユークリッドの互除法
date: 2021/04/07
---

## 説明
ax + by = gcd(a, b)を満たすx,yを求めます。

## 計算量
$$
O(log N)
$$

## 実装例
main関数内では[https://onlinejudge.u-aizu.ac.jp/courses/library/6/NTL/1/NTL_1_E](https://onlinejudge.u-aizu.ac.jp/courses/library/6/NTL/1/NTL_1_E)を解いています。

```cpp import=/assets/Library/math/extgcd.cpp
```

## 参考
> [https://qiita.com/drken/items/b97ff231e43bce50199a](https://qiita.com/drken/items/b97ff231e43bce50199a)  
> [https://qiita.com/oha-yashi/items/aa98a8e31633450967ab](https://qiita.com/oha-yashi/items/aa98a8e31633450967ab)
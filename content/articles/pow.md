---
title: Power
description: 数学 べき乗
date: 2021/04/11
---

## 説明
$a^{e}$を求めます。

**流れ**  
指数が偶数の場合は  
$a^{e} = a^{e / 2} \times a^{e / 2}$を計算します。

指数が奇数の場合は  
$a^{e} = a^{e - 1} \times a$を計算します。

## 計算量
$$
O(logN)
$$

## 実装例

```cpp import=/assets/Library/math/pow.cpp
```

> [https://atcoder.jp/contests/atc002/tasks/atc002_b](https://atcoder.jp/contests/atc002/tasks/atc002_b)
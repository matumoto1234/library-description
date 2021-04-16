---
title: Power
description: 数学 べき乗
date: 2021/04/16
---

## 説明
$a^{e}$を求めます

**アルゴリズム**  
- 指数が偶数の場合  
  $a^{e} = a^{\frac{e}{2}} \times a^{\frac{e}{2}}$を計算します  
  このときに一方を求めて掛け合わせることでもう一方を求める手順が減ります
- 指数が奇数の場合  
  $a^{e} = a^{e - 1} \times a$を計算します

## 計算量
$$
O(logN)
$$

## 実装例

```cpp import=/assets/Library/math/pow.cpp
```

## 参考
> [https://atcoder.jp/contests/atc002/tasks/atc002_b](https://atcoder.jp/contests/atc002/tasks/atc002_b)
---
title: ModPower
description: 数学 合同式でのべき乗
date: 2021/04/16
---

## 説明
$a^{e} \pmod p$を求めます

**アルゴリズム**  
- 指数が偶数の場合  
  $a^{e} = a^{\frac{e}{2}} \times a^{\frac{e}{2}}$を計算します  
  このときに一方を求めて掛け合わせることでもう一方を求める手順が減ります
- 指数が奇数の場合  
  $a^{e} = a^{e - 1} \times a$を計算します

<br>

上記の演算を合同式上で行います

- 指数が偶数の場合  
  $a^{e} \equiv a^{\frac{e}{2}} \times a^{\frac{e}{2}} \pmod p$
- 指数が奇数の場合  
  $a^{e} \equiv a^{e - 1} \times a \pmod p$


## 計算量
$$
O(logN)
$$

## 実装例

##### main関数内で解いている問題
> [https://atcoder.jp/contests/atc002/tasks/atc002_b](https://atcoder.jp/contests/atc002/tasks/atc002_b)

```cpp import=/assets/Library/math/modpow.cpp
```
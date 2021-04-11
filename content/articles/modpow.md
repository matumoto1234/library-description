---
title: ModPower
description: 数学 合同式でのべき乗
date: 2021/04/11
---

## 説明
$a^{e} \pmod p$を求めます。

**流れ**  
指数が偶数の場合は  
$a^{e} = a^{e / 2} \times a^{e / 2}$を計算します。

指数が奇数の場合は  
$a^{e} = a^{e - 1} \times a$を計算します。


<br>

上記の演算を合同式上で行います。

- 指数が偶数の場合  
$a^{e} \equiv a^{e \div 2} \times a^{e \div 2} \pmod p$
- 指数が奇数の場合  
$a^{e} \equiv a^{e \div 2} - 1 \pmod p$


## 計算量
$$
O(logN)
$$

## 実装例

```cpp import=/assets/Library/math/modpow.cpp
```

## 参考
> [https://atcoder.jp/contests/atc002/tasks/atc002_b](https://atcoder.jp/contests/atc002/tasks/atc002_b)

---
title: Divisor
description: 数学 約数列挙
date: 2021/04/16
---

## 説明
約数を列挙します

**アルゴリズム**  
1. $\sqrt{N}$までの数で$N$を割り切れるか判定します
2. $N$を割り切れた数を$a$としたとき, $a$は約数です
3. $\sqrt{N} \neq a$であるとき, $\frac{N}{a}$もまた約数です

<br>

**正当性**  
正の整数$N$が与えられたときに
$$
N=a \times b
$$
という風な形にできたとすると$a$が$\sqrt{N}$以上のとき、bは必ず$\sqrt{N}$以下です  
($a$, $b$両方が$\sqrt{N}$より大きいとすると$a\times b$は$N$より大きくなってしまうため)

そのため$\sqrt{N}$まで割り切れるかどうかを判定することで全ての約数を列挙できます

## 計算量
$$
O(\sqrt{N})
$$

## 実装例

```cpp import=/assets/Library/math/divisor.cpp
```

---
title: EulerPhi
description: 数学 オイラーのφ関数
date: 2021/04/16
---

## 説明
$1$から$N$までの自然数の内, $N$と互いに素な数の個数を求めます  

**アルゴリズム**  
$N = 30$を例とします  
$1$から$30$までの整数の中で$2$の倍数のものは$15$個あります  
$2$の倍数でない$15$個の内, $3$の倍数であるものは$5$個あります  
$3$の倍数でもない$10$個の内,$5$の倍数であるものは$2$個あります  
残った$8$個が$30$と互いに素な数の個数です

## 計算量
$$
O(\sqrt{N})
$$

## 実装例

##### main関数内で解いている問題
> [https://onlinejudge.u-aizu.ac.jp/courses/library/6/NTL/1/NTL_1_D](https://onlinejudge.u-aizu.ac.jp/courses/library/6/NTL/1/NTL_1_D)

```cpp import=/assets/Library/math/eulerphi.cpp
```

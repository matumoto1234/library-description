---
title: PrimeFactor
description: 数学 素因数列挙
date: 2021/04/11
---

## 説明
素因数を列挙します。

**流れ**
正の整数Nが与えられたときに
$$
N=a \times b
$$
という風な形にできたとするとaが$\sqrt{N}$以上のとき、bは必ず$\sqrt{N}$以下です。  
(a,b両方が$\sqrt{N}$より大きいとするとa$\times$bはNより大きくなってしまうため)

そのため$\sqrt{N}$まで割り切れるかどうかを判定することで全ての約数を列挙できます。

## 計算量
$$
O(\sqrt{N})
$$

## 実装例

```cpp import=/assets/Library/math/primefactor.cpp
```

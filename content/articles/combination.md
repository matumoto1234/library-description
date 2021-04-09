---
title: Combination
description: 数学 組み合わせ
date: 2021/04/07
---

## 説明
$nCr$を求めます。  

**なぜ演算途中で割り算をしても良いのか**  
res/1,res/2,res/3,...とループしていきますが、resにはn,n-1,n-2,...といった数が掛けられています。  
n,n-1はどちらかが2の倍数なので2で割り切れます。  
n,n-1,n-2はどれかが3の倍数なので3で割り切れます。

## 計算量
$$
O(r)
$$

## 実装例

```cpp import=/assets/Library/math/combination.cpp
```

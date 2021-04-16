---
title: Sieve of Eratosthenes
description: 数学 エラトステネスの篩
date: 2021/04/16
---

## 説明
$N$以下の非負整数$i$が素数であるかどうかを持った素数テーブルを構築します

ある数$N$以下のどの素数でも割り切れないならば$N$は素数であるという事実を用います

**アルゴリズム**  
1. 全ての要素の値を$true$にします
2. $2$からループを始めます
3. 素数の倍数を$false$にします
4. 次の数に進み, $true$であれば(3), $false$であれば進み続けます

<br>

**計算量がO(NloglogN)**  
素数$N$の逆数和は$loglogN$程度であると知られています

## 計算量
$$
O(NloglogN)
$$

## 実装例

```cpp import=/assets/Library/math/sieve.cpp
```

## 参考
> [https://manabitimes.jp/math/92](https://manabitimes.jp/math/92)

> [https://mikan-alpha.hatenablog.com/entry/2020/07/29/21034](https://mikan-alpha.hatenablog.com/entry/2020/07/29/21034)

> [https://manabitimes.jp/math/99](https://manabitimes.jp/math/99)
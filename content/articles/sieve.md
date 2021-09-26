---
title: Sieve of Eratosthenes
description: 数学 エラトステネスの篩
date: 2021/09/26
---

## 説明
$N$ 以下の自然数 $i$ が素数であるかどうかを持った素数テーブルを構築します

ある数 $N$ 以下のどの素数でも割り切れないならば $N$ は素数であるという事実を用います


**アルゴリズム**  
1. $1$ から $N$ までの要素の値を $true$ に初期化します
2. $N$ 以下の素数 $i$ についてループを回します
3. 素数 $i$ の倍数番目の値を $false$ にします

<br>

疑似コード
```cpp
sieve[1 から N] = true;
for (i : 素数) {
  for (j : 素数の倍数) {
    sieve[j] = false;
  }
}
```

<br>

**計算量の $\log \log N$ とは？**  
$N$ までの素数の逆数和は $\log \log N$ 程度と知られています

## 計算量
$$
O(N \log \log N)
$$

## 実装例

```cpp import=/assets/Library/math/sieve.cpp
```

## 参考
> [https://manabitimes.jp/math/92](https://manabitimes.jp/math/92)

> [https://mikan-alpha.hatenablog.com/entry/2020/07/29/21034](https://mikan-alpha.hatenablog.com/entry/2020/07/29/21034)

> [https://manabitimes.jp/math/99](https://manabitimes.jp/math/99)
---
title: PrimeFactorTable
description: 数学 素因数分解テーブル
date: 2021/09/26
---

## 説明
エラトステネスの篩の要領で $1$ から $N$ までの値の最小素因数を前計算してから素因数分解を行います  
$osa_k$ 法や、高速素因数分解などとも呼ばれます

$1$ から $N$ について $i$ 番目の数の最小素因数を `data[i]` に入れておくことで `i /= data[i]` と辿っていくことで高速に素因数分解ができます  

## 計算量
$$
<O(N \log \log N), O(\log N)>
$$

## 実装例

```cpp import=/assets/Library/math/primefactortable.cpp
```

## 参考

> [https://algo-logic.info/prime-fact](https://algo-logic.info/prime-fact)
> [https://osak.jp/diary/diary_201310.html#2013101](https://osak.jp/diary/diary_201310.html#2013101)
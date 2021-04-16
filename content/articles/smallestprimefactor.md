---
title: SmallestPrimeFactor
description: 数学 最小素因数分解
date: 2021/04/16
---

## 説明
エラトステネスの篩のように前計算してから素因数分解を行います  
$osak$法とも呼ばれるようです

$N$の最小素因数を$data[N]$に入れておくことで$N=N/data[N]$と辿っていくことで高速に素因数分解ができます  
素数の倍数をループする際にその素数を配列に格納していき, 今後変更しないようにします

## 計算量
構築$O(NloglogN)$  
素因数分解$O(logN)$

## 実装例

```cpp import=/assets/Library/math/smallestprimefactor.cpp
```

## 参考

> [https://algo-logic.info/prime-fact](https://algo-logic.info/prime-fact)
> [https://osak.jp/diary/diary_201310.html#2013101](https://osak.jp/diary/diary_201310.html#2013101)
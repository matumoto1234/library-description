---
title: Sieve of Eratosthenes
description: 数学 エラトステネスの篩
date: 2021/04/13
---

## 説明
N以下の非負整数iが素数であるかどうかを持った素数テーブルを構築します。

ある数N以下のどの素数でも割り切れないならばNは素数であるという事実を用います。

**流れ**  
1. 全ての要素の値をtrueにします。
2. 2からループを始めます。
3. 素数の倍数をfalseにします。
4. 次の数に進み、trueであれば(3)、falseであれば進み続けます。

<br>

**計算量がO(NloglogN)**  
素数Nの逆数和はloglogN程度であると知られています。[^1]

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
> [^1]: [https://manabitimes.jp/math/99](https://manabitimes.jp/math/99)
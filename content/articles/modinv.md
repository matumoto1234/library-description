---
title: ModInverse
description: 数学 合同式での逆元
date: 2021/04/11
---

## 説明
合同式上での逆元を求めます  
拡張ユークリッドの互除法を使って求めています

$a^{-1} \pmod p$を計算することを  
$ax + py = 1$を満たす$x$を求めるというように以下のようにして言い換えます

$$
a \times a^{-1} \equiv 1 \pmod p
$$
$a^{-1}$を$x$と置くと  
$$
a \times x \equiv 1 \pmod p
$$
$p$が法の合同式では$p$の倍数を足し引きしても合同なので  
$$
a \times x + py \equiv 1 \pmod p
$$
変形すると  
$$
ax + py = 1
$$
となります

**適応条件**  
$a^{-1} \pmod p$を計算する場合$a$と$p$が互いに素であれば求まります

## 計算量
$$
O(logN)
$$

## 実装例

```cpp import=/assets/Library/math/modinv.cpp
```

## 参考
> [https://drken1215.hatenablog.com/entry/2018/06/08/210000](https://drken1215.hatenablog.com/entry/2018/06/08/210000)
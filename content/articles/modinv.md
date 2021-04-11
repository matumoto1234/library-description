---
title: ModInverse
description: 数学 合同式での逆元
date: 2021/04/07
---

## 説明
合同式上での逆元を求めます。

`extgcd`を使って求めています。

こちらのサイトが参考になります。  
> [https://drken1215.hatenablog.com/entry/2018/06/08/210000](https://drken1215.hatenablog.com/entry/2018/06/08/210000)

$a^{-1} \pmod p$を計算することを  
$ax + py = 1$を満たすxを求めるというように言い換えます。

$a \times a^{-1} \equiv 1 \pmod p$なので、
$a^{-1}$を$x$と置くと、  
$a \times x \equiv 1 \pmod p$であり、  
pが法の合同式ではpの倍数を足し引きしても合同なので、  
$a \times x + py \equiv 1 \pmod p$  となり、
変形すると、  
$ax + py = 1$となります。

## 計算量
$$
O(logN)
$$

## 実装例

```cpp import=/assets/Library/math/modinv.cpp
```

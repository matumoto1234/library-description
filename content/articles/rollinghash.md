---
title: RollingHash
description: 文字列 ローリングハッシュ
date: 2021/04/13
---

## 説明
ローリングハッシュをします。

**文字列判定の流れ**  
文字列s,tに対してsの中にtが含まれているかを判定します。  
1. 文字列tに対してハッシュ値を決めます。
2. sの中から文字列tの長さ分取り出してハッシュ値が同じかどうか判定します。
3. 同じでなければ1文字分ずらして(2)から繰り返します。


**ハッシュについて**  
"aaa"に1という値を割り振ったとすると、"bbaaabb"という文字列の3文字目から5文字目の"aaa"も値は1になり、同じであると分かります。  
異なる文字列であるのに値が被ってしまうと誤って判定してしまうので大きい値を使う必要があります。  

ある文字列sに対して$B^0 \times s_0 + B^1 \times s_1 + B^2 \times s_2 + ... \pmod p$とすることでハッシュ値を決めています。  
ここで合同式の法となる値ですが、$2^{61} - 1$を推奨しています。[^1]  

文字列sの1文字目以降のハッシュ値を考えてみると  
$B^1 \times s_1 + B^2 \times s_2 + ... \pmod p$  
というようになります。  

文字列tのハッシュ値は  
$B^0 \times t_0 + B^1 \times t_1 + ... \pmod p$  
なので、$B$の指数が一致しないので値が同じかどうか判定できません。  
そこで、$B^{-1}$を文字列sのハッシュ値に掛けることにより指数を一致させます。  
この$B^{-i}(0 ≤ i ≤ N)$も前計算しておくことで求まります。  
具体的にはオイラーの小定理より  
$$
a^{p-1} \equiv 1 \pmod p 
$$
$$
a^{p-2} \times a \equiv 1 \pmod p
$$
となり、$a^{p-2}$がaの逆元であることが分かります。  
$a^{n}$の逆元は$a^{n(p-2)}$であるので繰り返し二乗法を用いて$O(logN)$で求めた後、  
$a$を掛けていって$a^{n-1}$の逆元,$a^{n-2}$の逆元,...と求めていきます。

ハッシュの値を累積和として前計算することで判定の際には$O(1)$でハッシュの値を求めることができます。

**基数はランダムな値**  
実装例では基数をランダムな値としています。  
詳しくはページ下部の参考欄をお読みください。

## 計算量
$$
O(N+M)
$$

## 実装例

```cpp import=/assets/Library/string/rollinghash.cpp
```

## 参考
> [https://onlinejudge.u-aizu.ac.jp/courses/lesson/1/ALDS1/14/ALDS1_14_](https://onlinejudge.u-aizu.ac.jp/courses/lesson/1/ALDS1/14/ALDS1_14_)
> [https://maspypy.com/rolling-hash%e3%81%ab%e3%81%a4%e3%81%84%e3%81%a6%ef%bc%88survey-%e7%a0%94%e7%a9%b6%ef%bc%8](https://maspypy.com/rolling-hash%e3%81%ab%e3%81%a4%e3%81%84%e3%81%a6%ef%bc%88survey-%e7%a0%94%e7%a9%b6%ef%bc%8)
> [https://www.slideshare.net/nagisaeto/rolling-hash-14999090](https://www.slideshare.net/nagisaeto/rolling-hash-14999090)
> [^1]: [https://qiita.com/keymoon/items/11fac5627672a6d6a9f](https://qiita.com/keymoon/items/11fac5627672a6d6a9f) 
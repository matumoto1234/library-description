---
title: RollingHash
description: 文字列 ローリングハッシュ
date: 2021/04/16
---

## 説明
ローリングハッシュをします

**文字列判定の流れ**  
文字列$s,t$に対して$s$の中に$t$が含まれているかを判定します  
1. 文字列$t$に対してハッシュ値を決めます
2. $s$の中から文字列$t$の長さ分取り出してハッシュ値が同じかどうか判定します
3. 同じでなければ$1$文字分ずらして(2)から繰り返します

<br>

<details><summary>ハッシュ値について</summary>

仮に"aaa"に$1$という値を割り振ったとします

"bbaaabb"という文字列の$3$文字目から$5$文字目の"aaa"もハッシュ値は$1$になり, ハッシュ値が同じであれば文字列も同じであると判定します  

ただし, 異なる文字列であるのに値が被ってしまうと誤った判定をしてしまうので値域を大きく取る必要があります  

<br>

**ハッシュ値の計算方法**  
ある文字列$s$に対して
$$
B^0 \times s_0 + B^1 \times s_1 + B^2 \times s_2 + ... \pmod p
$$
とすることでハッシュ値を計算しています  
ここで合同式の法となる値ですが, $2^{61} - 1$を推奨しています  
※ 詳しい理由についてはページ下部の参考欄をご覧ください

文字列$s$の$1$文字目以降のハッシュ値を考えてみると  
$B^1 \times s_1 + B^2 \times s_2 + ... \pmod p$  
というようになります  

文字列$t$のハッシュ値は  
$B^0 \times t_0 + B^1 \times t_1 + ... \pmod p$  
なので$B$の指数が一致しないため値が同じかどうか判定できません  
そこで, $B^{-1}$を文字列$s$のハッシュ値に掛けることにより指数を一致させます  

文字列$s$の$i$文字目以降のハッシュ値も同様に$B^{-i}$を掛けます  
この$B^{-i}(0 ≤ i ≤ N)$も前計算しておくことで求まります  

<details><summary>i番目の逆元の前計算</summary>

オイラーの小定理より  
$$
a^{p-1} \equiv 1 \pmod p 
$$
$$
a^{p-2} \times a \equiv 1 \pmod p
$$
となり, $a^{p-2}$が$a$の逆元であることが分かります  
$a^{n}$の逆元は$a^{n(p-2)}$であるので繰り返し二乗法を用いて$O(logN)$で求めた後  
$a$を掛けていって$a^{n-1}$の逆元,$a^{n-2}$の逆元,...と求めていきます
</details>


<br>

ハッシュの値を累積和として前計算することで判定の際には$O(1)$でハッシュの値を求めることができます

</details>

<br>

**基数はランダムな値**  
実装例では基数をランダムな値としています  
詳しくはページ下部の参考欄をお読みください

## 計算量
$$
O(N+M)
$$

## 実装例

##### main関数内で解いている問題
> [https://onlinejudge.u-aizu.ac.jp/courses/lesson/1/ALDS1/14/ALDS1_14_B](https://onlinejudge.u-aizu.ac.jp/courses/lesson/1/ALDS1/14/ALDS1_14_B)  

```cpp import=/assets/Library/string/rollinghash.cpp
```

## 参考

> [https://maspypy.com/rolling-hash%e3%81%ab%e3%81%a4%e3%81%84%e3%81%a6%ef%bc%88survey-%e7%a0%94%e7%a9%b6%ef%bc%8](https://maspypy.com/rolling-hash%e3%81%ab%e3%81%a4%e3%81%84%e3%81%a6%ef%bc%88survey-%e7%a0%94%e7%a9%b6%ef%bc%8)  

> [https://www.slideshare.net/nagisaeto/rolling-hash-14999090](https://www.slideshare.net/nagisaeto/rolling-hash-14999090)  

> [https://qiita.com/keymoon/items/11fac5627672a6d6a9f](https://qiita.com/keymoon/items/11fac5627672a6d6a9f) 
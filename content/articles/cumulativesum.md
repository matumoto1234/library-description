---
title: CumulativeSum
description: データ構造 累積和
date: 2021/04/07
---

## 説明
累積和をします。

query(l,r)で左端lから右端rまでの総和を求めます。  
実装例では[l,r)でクエリを扱っています。

**実装例の説明**  
累積和は元の配列aのlからrまでの総和を前計算をすることで高速に求めることができます。  

例えば、
a<sub>0</sub> a<sub>1</sub> a<sub>2</sub> a<sub>3</sub>  
とあったときに、a<sub>2</sub>からa<sub>3</sub>の和を求めるとします。

求めたいものは a<sub>2</sub> + a<sub>3</sub> ですが、あらかじめ前計算として値を順に足した配列sumを用意します。

sum<sub>0</sub> = a<sub>0</sub>  
sum<sub>1</sub> = a<sub>0</sub> + a<sub>1</sub>  
sum<sub>2</sub> = a<sub>0</sub> + a<sub>1</sub> + a<sub>2</sub>  
sum<sub>3</sub> = a<sub>0</sub> + a<sub>1</sub> + a<sub>2</sub>  + a<sub>3</sub>

sum<sub>3</sub>からsum<sub>1</sub>を引けば求めたいものが求まるのがわかると思います。

sum<sub>i</sub>はi番目までの値を0から足したものなので、sum<sub>r</sub>(r番目まで足したもの)からsum<sub>l</sub>(l番目までを足したもの)を引くとl+1番目からr番目まで足したものが残ります。

<br>

**おまけ**  
これを実装例のように半開区間にして扱いやすくするには  
sum<sub>i</sub>をi-1番目まで足したものとして扱います。

先ほどの例を使うと  
sum<sub>0</sub> = 0  
sum<sub>1</sub> = a<sub>0</sub>  
sum<sub>2</sub> = a<sub>0</sub> + a<sub>1</sub>  
sum<sub>3</sub> = a<sub>0</sub> + a<sub>1</sub> + a<sub>2</sub>  
sum<sub>4</sub> = a<sub>0</sub> + a<sub>1</sub> + a<sub>2</sub>  + a<sub>3</sub>

先頭に0を入れることで添え字を一つずらすことができます。

## 計算量
構築 $O(N)$  
クエリ $O(1)$

## 実装例

```cpp import=/assets/Library/data-structure/cumulativesum.cpp
```

---
title: BinarySearch
description: データ構造 二分探索
date: 2021/04/16
---

## 説明
有効な値と有効でない値の境界を二分探索して求めます  


二分探索は,データの大小関係を利用した高速な探索アルゴリズムです

区間を半分,半分,半分,...としていくことで求めます  
1. 左端と右端の中央の値が有効かどうかを判定する  
   - 有効であれば有効な端を中央の値にする  
   - 有効でなければ有効でない端を中央の値にする  
2. 終了条件まで繰り返す

操作(1)で区間の長さが半分になるため,高速に求めることができます

また,二分探索を実装する際に$[l, r]$までの区間の扱いを半開区間$[l, r+1)$とすると筋の良い実装になるというテクニックがあります

<details><summary>二分探索の計算量について</summary>

二分探索の計算量は$O(logN)$です

<br>

**なぜlogが出てくるのか**  
これは長さ$N$の区間を$\frac{1}{2}$倍,$\frac{1}{2}$倍,$\frac{1}{2}$倍...としていくときに$1$になるまで$\frac{1}{2}$倍する回数が $logN$回くらいだからです

<br>

**なんでlogN回くらいなのか**  
これは <u>$1$を$N$以上にするまでに何回$2$倍するか</u> と考えるとわかりやすくなると思います

$1$ → $2$ → $4$ → $8$ →...  
と$2$倍していくといずれ$N$を超えると思います

$$
2^{x} ≥ N
$$
となる$x$を求めたいです  
この$x$は$log$を使って求めることができます

<br>

<details><summary>logについて</summary>

$$
a^{b}= c
$$  

というときに$a$の なんちゃら 乗が$c$となるような$b$を求めるものです  
例えば$a=2$,$c=8$だったときに  
$$
2^b=8
$$
となるような$b$を$log$を使って求めることができます  
$$
b=log_{2}8
$$
といった感じです  
この場合の$b$は  
$$
b=log_{2}2^{3}
$$
$$
b=3 \times log_{2}2
$$
$$
b=3
$$
となって$b$が$3$と求まります  
</details>

<br>


$$
x ≥ log_{2}N
$$
つまり,$1$を$2$倍,$2$倍,$2$倍,...という操作を$log_2N$回行えば$N$を超える数になります  
計算量としては$log_2N$回なのですがわかりやすい形に整えるため,底の変換公式を利用します

$$
log_{2}N
$$
底の変換公式を使うと
$$
log_{2}N = {\frac{log_{e}N}{log_{e}2}}
log_{2}N = {\frac{1}{log_{e}2}\times log_{e}N}
$$

とすることができ,定数をくくりだせました

これで$1$を$N$が超えるまで$2$倍,$2$倍,$2$倍...としていったときの操作回数は$logN$回であることが分かったので,$N$を$\frac{1}{2}$倍,$\frac{1}{2}$倍,$\frac{1}{2}$倍...としていったときの操作回数も$logN$回です

</details>

<br>

**実装例の説明**  
コンストラクタ  
```cpp
(1) BinarySearch<S, is_valid> bs
(2) BinarySearch<S, is_valid> bs(valid, invalid)
```
- 型$S$
- 判定関数bool is_valid($S$ mid, $S$ target)

を定義する必要があります  

例として,配列$v$の中で$target$以上で最小の値を探索する場合は以下のようになります
```cpp
bool is_valid(int mid, int target){
   return v[mid]>=target;
}

BinarySearch<int, is_valid> bs(n,-1); // bs(valid, invalid)
```

関数の第一引数では探索する値,第二引数では目的となる値を同じ型で入れます  
$set\_valid$関数もしくは変数生成時に二分探索での初期値を入れます  
$build$関数を呼び出します

## 計算量
$$
O(logN)
$$

## 実装例

##### main関数内で解いている問題
> [https://onlinejudge.u-aizu.ac.jp/courses/lesson/1/ALDS1/4/ALDS1_4_B](https://onlinejudge.u-aizu.ac.jp/courses/lesson/1/ALDS1/4/ALDS1_4_B)

```cpp import=/assets/Library/data-structure/binarysearch.cpp
```

## 参考
> [https://qiita.com/drken/items/872ebc3a2b5caaa4a0d0#%E4%BE%8B-7-%E3%83%8A%E3%83%99%E3%82%A2%E3%83%84-ologn](https://qiita.com/drken/items/872ebc3a2b5caaa4a0d0#%E4%BE%8B-7-%E3%83%8A%E3%83%99%E3%82%A2%E3%83%84-ologn)

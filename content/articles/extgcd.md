---
title: ExtendedEuclideanAlgorithm
description: 数学 拡張ユークリッドの互除法
date: 2021/04/16
---

## 説明
$ax + by = \gcd(a, b)$を満たす$x,$y$を再帰的に求めます

**使い方**  
次のような例を見ていきます  
$$
111x + 30y = 12
$$
となる$x$と$y$を求めたいです  

まず, $\gcd(111, 30)$は$3$です  
※ ここでの$\gcd(a, b)$というのは$a$と$b$の最大公約数のことを指します  
拡張ユークリッドの互除法で求めることができるのが$ax+by=\gcd(a,b)$の$x$と$y$なので$111x+30y=3$を先に求めます

<br>

以下のように使うと$x$と$y$という変数に条件を満たす数がそれぞれ代入されます
```cpp
int x,y;
extgcd(111, 30, x, y);
```
今回の例では $x=3, y=-11$ と求まります  
よって,  
$$
111x + 30y = 3
$$
$$
111 \times 3 + 30 \times -11 = 3
$$
$$
111 \times 12 + 30 \times -44 = 12
$$
$x=12, y=-44$となり求めることができました

<br>

### extgcdのやっていること

一言で言えば, 式変形を再帰的に動かしています

$$
a = qb + r
$$

$$
ax + by = \gcd(a,b)
$$

$$
(qb + r)x + by = \gcd(a,b)
$$

$$
qbx + rx + by = \gcd(a,b)
$$

$$
(qx + y)b +rx = \gcd(a,b)
$$

$s, t$を
$s=qx + y$  
$t=x$  
というようにおくことで
$$
bs + rt = \gcd(a,b)
$$
のように表現できます

次に,$s,t$で$x,y$を表します

$$
t=x
$$
$$
x=t
$$

<br>
<br>

$$
s=qx+y
$$

$$
s-qx=y
$$

$$
y=s-qx
$$

$$
y=s-qt
$$

以上から$s,t$が求りさえすれば$x,y$が求まり, それぞれ値を代入できます

<br>

### どのようにs,tは求まるのか

- 式変形  
  $(qx + y)b +rx = \gcd(a,b)$
- プログラム
```cpp
int extgcd(int a, int b, int &x, int &y){
    if(b==0){
        x=1;
        y=0;
        return a;
    }
    int q = a/b;
    int r = a%b;
    int s, t;
    int d = extgcd(b, r, s, t)
    x = t;
    y = s - q * x;
    return d;
}
```

注目してほしいのは$a$と$b$の移り変わりです

$(a,b)$ → $(b,a\%b)$

という風に変化しています  
これはまさしくユークリッドの互除法です  
そして, 終了条件である<u>if(b == 0)</u>というのもユークリッドの互除法の終了条件と同じです  
ユークリッドの互除法で<u>b==0</u>となるときは$a$が最大公約数でした

$$
ax+by=\gcd(a,b)
$$

のbが0だったとき

$$
ax=\gcd(a,b)
$$

$a$が最大公約数なので

$$
\gcd(a,b)x=\gcd(a,b)
$$

よって
$x=1$

$y$はここで$0$としておきます  
数学的には$y$はなんでも良く, <u>b==0</u>のときに$y=100$や$y=-50$などにしても値は変わってきますが条件を満たす$x,y$は問題なく求まります  
しかし,$y=0$とすることによって$|x|+|y|$が解の中で最小のものになります

以上より, 再帰的に解く中で<u>b==0</u>となり$x=1,y=0$となって$s,t$は求まります

## 計算量
$$
O(log N)
$$

## 実装例

##### main関数内で解いている問題
> [https://onlinejudge.u-aizu.ac.jp/courses/library/6/NTL/1/NTL_1_E](https://onlinejudge.u-aizu.ac.jp/courses/library/6/NTL/1/NTL_1_E)

```cpp import=/assets/Library/math/extgcd.cpp
```

## 参考
> [https://qiita.com/drken/items/b97ff231e43bce50199a](https://qiita.com/drken/items/b97ff231e43bce50199a)  
> [https://qiita.com/oha-yashi/items/aa98a8e31633450967ab](https://qiita.com/oha-yashi/items/aa98a8e31633450967ab)
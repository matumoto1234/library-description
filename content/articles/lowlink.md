---
title: LowLink
description: グラフ 橋/間接点の列挙
date: 2021/04/07
---

## 説明
橋/間接点を求めます  

- 橋とは  
  取り除くとグラフが非連結になる辺
- 間接点とは  
  取り除くとグラフが非連結になる頂点

<br>

間接点であるかどうかの判定は木の性質を使うことで効率よく判定することができます  

木の重要な性質として<u>任意の2頂点間の経路は一つに定まる</u>というものがあります  
与えられたグラフを深さ優先探索をすることで木を作ります  
深さ優先探索で通らなかった辺を後退辺と呼びます  
深さ優先探索によって得られた順番$(order)$を用いて$lowlink$を次のように定義します
```
lowlink := 子方向の辺を使って辿り着ける頂点もしくは後退辺だけを1回以下通って辿り着ける頂点のorderの最小値
```

この$lowlink$を用いて次のように判定します

<br>

間接点であるかどうかの条件  
 - 根である場合は子が$2$つ以上であるか
 - 根ない場合は$order[v] ≤ lowlink[child]$となる子$child$がいるか

 <br>

 橋であるかどうかの条件  
  - $order[v] ≤ lowlink[child]$となる子$child$がいるか

## 計算量
$$
O(V+E)
$$

## 実装例

```cpp import=/assets/Library/graph/lowlink.cpp
```

## 参考
> [https://www.npca.jp/works/magazine/2014](https://www.npca.jp/works/magazine/2014)
> [https://onlinejudge.u-aizu.ac.jp/courses/library/5/GRL/3/GRL_3_A](https://onlinejudge.u-aizu.ac.jp/courses/library/5/GRL/3/GRL_3_A)
> [https://onlinejudge.u-aizu.ac.jp/courses/library/5/GRL/3/GRL_3_B](https://onlinejudge.u-aizu.ac.jp/courses/library/5/GRL/3/GRL_3_B)
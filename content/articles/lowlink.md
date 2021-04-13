---
title: LowLink
description: グラフ 橋/間接点の列挙
date: 2021/04/07
---

## 説明
橋/間接点を求めます。  

`取り除くとグラフが非連結になる頂点`のことを間接点といい、`取り除くとグラフが非連結になる辺`のことを橋といいます。

間接点であるかどうかの判定は、木の性質を使うことで効率よく判定することができます。  
木の重要な性質として、`任意の2頂点間の経路は一つに定まる`というものがあります。  
与えられたグラフをDFSをすることで木を作ります。  
DFSで通らなかった辺を後退辺と呼びます。  
DFSによって得られた順番(order)を用いてlowlinkを次のように定義します。
```
lowlink := 子方向の辺を使って辿り着ける頂点もしくは後退辺だけを1回以下通って辿り着ける頂点のorderの最小値
```

間接点であるかどうかの条件は  
 - 根である場合は子が2つ以上であるか
 - 根ない場合はorder[v] ≤ lowlink[child]となる子childがいるか

 橋であるかどうかの条件は  
  - order[v] ≤ lowlink[child]となる子childがいるか

## 計算量
$$
O(V+E)
$$

## 実装例

```cpp import=/assets/Library/graph/lowlink.cpp
```

## 参考
> [https://www.npca.jp/works/magazine/2014](https://www.npca.jp/works/magazine/2014)
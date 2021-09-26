---
title: BellmanFord
description: グラフ 単一始点最短経路
date: 2021/09/26
---

## 説明
単一始点最短経路を求めるアルゴリズムです  
負の閉路があると最短距離は求まりませんが検知することができます

**アルゴリズム**
1. 全ての頂点の距離を $INF$ で初期化します
2. 始点の距離を $0$ にします
3. 全ての辺に対して次のような操作を行い続けます  
  - 頂点 $from$ の距離 + $cost$ が頂点 $to$ の距離よりも小さいなら頂点 $to$ の距離を更新する  
4. (3)の操作が $V$ 回以上続いているならば負の閉路が存在する

(3)の操作が一回行われる度に最低でも一つの頂点の距離は確定します  
始点の距離は初めに確定しているので $V - 1$ 回(3)の操作を行うことで最短経路が確定します

<br>

疑似コード
```cpp
dist[全ての頂点] = INF
dist[始点] = 0
for (i : 頂点数) {
  for (e : 全ての辺) {
    if (dist[e.to] >= dist[e.from] + e.cost) {
      dist[e.to] = dist[e.from] + e.cost
    }
  }
}
```

**おまけの説明**  
実装例では閉路の検知の他に、その閉路が目的地 $g$ へと繋がっているかを判定しています  
$V$ 回以降の更新で頂点 $to$ の距離を $-INF$ にすることで必ず更新するようにします  
更新を $2 \times V$ 回まで行うことで閉路から目的地 $g$ へ繋がっていた場合は目的地 $g$ も更新されます

## 計算量
$$
O(VE)
$$

## 実装例

##### main関数内で解いている問題
> [https://onlinejudge.u-aizu.ac.jp/courses/library/5/GRL/1/GRL_1_B](https://onlinejudge.u-aizu.ac.jp/courses/library/5/GRL/1/GRL_1_B)

```cpp  import=/assets/Library/graph/bellmanford.cpp
```

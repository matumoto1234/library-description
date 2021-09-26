---
title: TopologicalSort
description: グラフ トポロジカルソート
date: 2021/04/16
---

## 説明
トポロジカルソートをします

**トポロジカルソートとは**  
有向グラフ $G$ の各頂点をある順序で訪れていったときに、すでに訪れた頂点に向かう辺が存在しないような順序のことです

**アルゴリズム**  
1. 入次数が$0$の頂点をキューに入れます
2. キューから頂点を取り出してその頂点から出る辺を取り除きます
3. 頂点をトポロジカルソートの頂点に加え,(1)から繰り返します

<br>

疑似コード

```cpp
queue.push(入次数が 0 の頂点集合)

while queue が空になるまで {
  vertex = queueから取り出した頂点

  for (to : vertex からたどり着ける未訪問の頂点) {
    queue.push(to)
  }
}
```

## 計算量
$$
O(V+E)
$$

## 実装例

##### main関数内で解いている問題
> [https://onlinejudge.u-aizu.ac.jp/courses/library/5/GRL/4/GRL_4_B](https://onlinejudge.u-aizu.ac.jp/courses/library/5/GRL/4/GRL_4_B)

```cpp import=/assets/Library/graph/topologicalsort.cpp
```

## 参考
> [https://hcpc-hokudai.github.io/archive/graph_scc_001.pdf](https://hcpc-hokudai.github.io/archive/graph_scc_001.pdf)
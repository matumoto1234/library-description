---
title: ConvertGraph
description: グラフ グリッドからグラフへ変換
date: 2021/04/6
---

## 説明
グリッドグラフを隣接グラフに変換します。  

縦3横3の平面があったとして
```
0 1 2
3 4 5
6 7 8
```
という風に左上から順に隣接するマスへ辺を貼ります。

## 計算量
$$
O(HW)
$$

## 実装例

```cpp import=/assets/Library/graph/convertgraph.cpp
```

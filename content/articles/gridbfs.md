---
title: GridBFS
description: グラフ グリッド上での幅優先探索
date: 2021/04/07
---

## 説明
グリッドグラフ上で指定した文字を始点として幅優先探索をします

**アルゴリズム**  
1. 始点のマスをキューに入れて探索を始めます 
2. キューからマスを取り出して隣接しているマスが訪問済みかどうかを調べます  
3. 訪問していない場合にそのマスの距離を記録し,マスをキューに入れます

(2)と(3)を繰り返すことで探索を進めていき,キューの中身がなくなったら終了です

## 計算量
$$
O(HW)
$$

## 実装例

```cpp import=/assets/Library/graph/gridbfs.cpp
```

## 参考
> [atcoder typical contest 002 A](https://atcoder.jp/contests/atc002/tasks/abc007_3)
---
title: LongestCommonSubsequence
description: 動的計画法 最長共通部分列
date: 2021/04/07
---

## 説明
最長共通部分列を求めます。

長さがnの配列Aと長さがmの配列Bがあったときに
```
dp[i][j] := 配列Aのi番目,配列Bのj番目までの最長共通部分列の長さ
```
とします。

求めたい答えは`dp[n-1][m-1]`に入っていることになります。

**流れ**  
1. `dp[0][j](0≤j<m)`を

## 計算量
$$
O(NM)
$$

## 実装例


```cpp import=/assets/Library/dp/longestcommonsubsequence.cpp
```

---
title: LongestCommonSubsequence
description: 動的計画法 最長共通部分列
date: 2021/04/16
---

## 説明
最長共通部分列を求めます

長さが$N$の配列$A$と長さが$M$の配列$B$があったときに
```
dp[i][j] := 配列Aのi番目,配列Bのj番目までの最長共通部分列の長さ
```
と定義します

そうすると求めたい答えは$dp[N][M]$に入っていることになります。

**アルゴリズム**  
- $dp[i-1][j-1]$
- $dp[i][j-1]$
- $dp[i-1][j]$

上記の三つが既に求まっているとき$dp[i][j]$の値を求めることができます

$A_{i}$と$B_{j}$が等しいか等しくないかで場合分けして考えます

<br>

 - $A_{i}$と$B_{j}$が等しい場合

($A_{i-1}$,$B_{j-1}$までの最長共通部分列の長さを$+1$したもの)が($A_{i}$,$B_{j}$までの最長共通部分列の長さ)になります  
```cpp
dp[i][j] = max(dp[i][j], dp[i-1][j-1])
```

<br>

 - $A_{i}$と$B_{j}$が等しくない場合

 ($A_{i-1},B_{j}$までの最長共通部分列の長さ)と($A_{i},B_{j-1}$までの最長共通部分列の長さ)の大きい方になります。  
 ```cpp
 dp[i][j] = max({dp[i][j], dp[i-1][j], dp[i-1][j]})
 ```
## 計算量
$$
O(NM)
$$

## 実装例

##### main関数内で解いている問題
> [https://atcoder.jp/contests/dp/tasks/dp_f](https://atcoder.jp/contests/dp/tasks/dp_f)

```cpp import=/assets/Library/dp/longestcommonsubsequence.cpp
```

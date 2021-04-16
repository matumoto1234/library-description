---
title: ShortestHamiltonianCycle
description: グラフ 最短ハミルトン閉路
date: 2021/04/16
---

## 説明
最短ハミルトン閉路のコストを求めます

**最短ハミルトン閉路とは**  
全ての頂点を一度だけ訪問し始点に戻ってくるような閉路のことを指します

**アルゴリズム**  
1. 始点から深さ優先探索をします
2. bit列によって訪問したかどうかを管理します
3. 全ての頂点に訪問済み かつ 始点に戻ってきたのであればそのコストを返します

深さ優先探索をする際にメモ化再帰を行うことで効率的に探索します

<details><summary>メモ化再帰について</summary>

再帰をする際に計算結果を保持しておくことで一度行った計算を省くことができます

例としてフィボナッチ数列の$N$項を以下のような再帰で解きます
```cpp
int fibo(int i){
  if(i==0||i==1) return 1;
  return fibo(i-1)+fibo(i-2);
}
```

上記のような再帰で$4$項の計算をしてみるとします  
(呼び出される関数を$\{\}$で囲みます)

- $fibo(4) = \{fibo(3)\} + fibo(2)$  

  - $fibo(3) = \{fibo(2)\} + fibo(1)$  

    - $fibo(2) = \{fibo(1)\} + fibo(0)$  

      - $fibo(1) = 1$

    - $fibo(2) = 1 + \{fibo(0)\}$

      - $fibo(0) = 1$

    - $fibo(2) = 1 + 1$

  - $fibo(3) = 2 + \{fibo(1)\}$

    - $fibo(1) = 1$

  - $fibo(3) = 2 + 1$

- $fibo(4) = 3 + \{fibo(2)\}$

  - $fibo(2) = \{fibo(1)\} + fibo(0)$

    - $fibo(1) = 1$

  - $fibo(2) = 1 + \{fibo(0)\}$

    - $fibo(0) = 1$

  - $fibo(2) = 1 + 1$

- $fibo(4) = 3 + 2$

<br>

計算途中で$fibo(2)$などが数回呼び出されることがありました  
これをメモ化再帰にするには以下のように書きます
```cpp
// memoは全て-1で初期化してたとします
int memo[10];

int fibo(int i){
  if(i==0||i==1) return 1;
  if(memo[i] != -1) return memo[i];

  memo[i]=fibo(i-1)+fibo(i-2);
  return memo[i];
}
```

計算結果を保持しておく場所を作っておきます  
初期値が変わっている場合は既に計算済みということなのでその結果を返します
</details>

## 計算量
$$
O(V2^{V})
$$

## 実装例

##### main関数内で解いている問題
> [https://onlinejudge.u-aizu.ac.jp/courses/library/7/DPL/2/DPL_2_A](https://onlinejudge.u-aizu.ac.jp/courses/library/7/DPL/2/DPL_2_A)

```cpp import=/assets/Library/graph/shortesthamiltoniancycle.cpp
```

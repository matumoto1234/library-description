---
title: Dijkstra
description: グラフ 単一始点最短経路
date: 2021/04/06
---

## 説明
単一始点最短経路を求めるアルゴリズムです。負の辺があっても負の閉路がなければ正しく動作します。  


## 計算量
頂点数をV,辺の数をEとすると
$$
O(ElogV)
$$

## 実装例
main関数内では[AOJ_GRL_1_A](https://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=GRL_1_A&lang=ja)を解いています。

```cpp
#include <bits/stdc++.h>
using namespace std;

template <typename T>
struct Dijkstra {
  struct edge {
    int to;
    T cost;
    edge() {}
    edge(int to, T cost) : to(to), cost(cost) {}
    bool operator<(const edge &e) const { return cost > e.cost; }
  };

  T inf() { return numeric_limits<T>::max()/2; }

  vector<vector<edge>> G;
  vector<T> ds;
  vector<int> bs;
  Dijkstra(int n) : G(n) {}

  void add_edge(int from, int to, T cost) { G[from].emplace_back(to, cost); }

  void build(int start) {
    int n = G.size();
    ds.assign(n, inf());
    bs.assign(n,-1);

    priority_queue<edge> Q;
    ds[start] = 0;
    Q.emplace(start, ds[start]);
    while (!Q.empty()) {
      auto p = Q.top();
      Q.pop();
      int v = p.to;
      if (ds[v] < p.cost) continue;
      for (auto e : G[v]) {
        if (ds[e.to] > ds[v] + e.cost) {
          ds[e.to] = ds[v] + e.cost;
          bs[e.to]=v;
          Q.emplace(e.to, ds[e.to]);
        }
      }
    }
  }

  T operator[](int k) { return ds[k]; }

  vector<int> restore(int to){
    vector<int> res;
    if(bs[to]<0){
      return res;
    }
    while(to!=-1){
      res.emplace_back(to);
      to=bs[to];
    }
    reverse(res.begin(),res.end());
    return res;
  }
};

int main() {
  using ll = long long;
  int v, e, r;

  cin >> v >> e >> r;
  Dijkstra<ll> G(v);

  for (int i = 0; i < e; i++) {
    int s, t, d;
    cin >> s >> t >> d;
    G.add_edge(s, t, d);
  }
  G.build(r);

  for (int i = 0; i < v; i++) {
    if (G[i] == G.inf()) {
      cout << "INF" << endl;
      continue;
    }
    cout << G[i] << endl;
  }
  return 0;
}
```
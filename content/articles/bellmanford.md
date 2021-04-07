---
title: BellmanFord
description: グラフ 単一始点最短経路
date: 2021/04/7
---

## 説明
単一始点最短経路を求めるアルゴリズムです。負の閉路があると最短距離は求まりませんが検知することができます。

**前提**
辺は頂点fromと頂点toを繋いでおり、それぞれcostを持っています。  
頂点は始点からの距離を持っています。

**流れ**
1. `全ての頂点の距離`をINFで初期化します。
2. `始点の距離`を0にします。
3. 全ての辺に対して次のような操作をV回行います。  
`頂点fromの距離+cost`が`頂点toの距離`よりも小さいなら`頂点toの距離`を更新する。
4. (3)の操作がV回以上続いているならば閉路がある。

(3)の操作が一回行われる度に最低でも`一つの頂点の距離`は確定します。  
これは最短経路が確定している頂点から伸びている辺を使うと


**実装例の説明**  
実装例では閉路の検知の他に、その閉路が目的地へと繋がっているかを判定しています。



## 計算量
$$
O(VE)
$$

## 実装例

```cpp
#include <bits/stdc++.h>
using namespace std;

template <typename T>
struct BellmanFord{
  struct edge {
    int from,to;
    T cost;
    edge(){}
    edge(int f,int t,T c):from(f),to(t),cost(c){}
  };

  int V;
  bool neg_cycle;
  bool neg_cycle_to_goal;
  vector<edge> es;
  vector<T> ds;

  BellmanFord(int N):V(N),neg_cycle(false),neg_cycle_to_goal(false){}

  void add_edge(int from,int to,T cost){ es.emplace_back(from,to,cost); }

  T inf() { return numeric_limits<T>::max()/2; }

  void build(int s,int g = -1){
    if(g==-1) g=V-1;
    ds.assign(V,inf());
    ds[s]=0;

    for(int i=0;i<2*V;i++){
      for(edge e : es){
        if(ds[e.from]>=inf()) continue;
        if(ds[e.to]<=ds[e.from]+e.cost) continue;

        ds[e.to]=ds[e.from]+e.cost;
        if(i>=V-1){
          ds[e.to]=-inf();
          neg_cycle=true;
          if(e.to==g){
            neg_cycle_to_goal=true;
            return;
          }
        }
      }
    }
  }

  T operator[](int k){ return ds[k]; }
};

int main() {
  int V,E,r;
  cin>>V>>E>>r;
  BellmanFord<ll> G(V);
  for(int i=0;i<E;i++){
    int s,t,d;
    cin>>s>>t>>d;
    G.add_edge(s,t,d);
  }
  G.build(r);
  if(G.neg_cycle){
    cout<<"NEGATIVE CYCLE"<<endl;
    return 0;
  }

  for(int i=0;i<V;i++){
    if(G[i]==G.inf()){
      cout<<"INF"<<'\n';
    }else{
      cout<<G[i]<<'\n';
    }
  }
}
```

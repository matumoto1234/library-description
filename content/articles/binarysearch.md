---
title: BinarySearch
description: データ構造 二分探索
date: 2021/04/07
---

## 説明
有効な値と有効でない値の境界を二分探索して求めます。  
<!--
<details>
<summary>二分探索について</summary>

二分探索は、データの大小関係を利用した高速な探索アルゴリズムです。

区間を半分,半分,半分,...としていくことで求めます。  
1. 左端と右端の中央の値が有効かどうかを判定する。  
  有効であれば有効な端を中央の値にする。  
  有効でなければ有効でない端を中央の値にする。
2. 終了条件まで繰り返す。

操作(1)で区間の長さが半分になるため、高速に求めることができます。

また、二分探索を実装する際に[l, r]までの区間の扱いを半開区間[l, r+1)とすると、筋の良い実装になるというテクニックがあります。

二分探索の計算量についてですが、$O(logN)$です。

<br>

**なぜlogが出てくるのか**  
例えば、計算量にlogが出てくるものといえば二分探索があります。区間を半分、半分、半分、...みたいにしていくものは大体logがつくと思っています。これは長さNの区間を1/2倍,1/2倍,1/2倍...としていくときに1になるまで1/2倍する回数が logN 回くらいだからです。

<br>

**なんでlogN回くらいなのか**  
これは <u>1をN以上にするまでに何回2倍するか</u> と考えるとわかりやすくなると思います。

1 → 2 → 4 → 8 →...  
と2倍していくといずれNを超えると思います。

つまり、  
2 <sup>x</sup> ≥ N
となる x を求めたいわけです。  

<br>

ところで、logの定義は覚えていますか？ logというのは  
$$a<sup>b</sup>= c$$
というときに、aの なんちゃら 乗がcとなるようなbを求めるものです。  
例えば、a=2,c=8だったときに  
$$2<sup>b</sup>=8$$
となるようなbを、logを使って求めることができます。  
$$b=log<sub>2</sub>8$$
といった感じです。この場合のbは  
$$b=log<sub>2</sub>2<sup>3</sup>  $$
$$b=3*log<sub>2</sub>2  $$
$$b=3$$
となって、bが3と求まります。  


logを復習したところでさっきの式を見てみましょう。  
$$2 <sup>x</sup> ≥ N$$

この x は  
$$x ≥ log<sub>2</sub> N$$
こんな風に求めることができます。つまり、1を2倍、2倍、2倍、...という操作をlog<sub>2</sub>N回行えばNを超える数になります。計算量としてはlog<sub>2</sub>N回なのですがわかりやすい形に整えるため、底の変換公式を利用します。

$$log<sub>2</sub>N$$
底の変換公式を使うと、  
$$
log<sub>2</sub>N = {\frac{log_e N}{log_e 2}}
log<sub>2</sub>N = {\frac{1}{log_e 2}\times log_e N}
$$

とすることができ、定数をくくりだせました。[^1]

これで1をNが超えるまで2倍、2倍、2倍...としていったときの操作回数はlogN回であることが分かったので、Nを1/2倍、1/2倍、1/2倍...としていったときの操作回数もlogN回です。

</details>
-->

<br>

**実装例の説明**  
あらかじめis_validという関数を作成しておき、テンプレート引数に関数ポインタとして渡します。  
is_validの第一引数では探索する値、第二引数では目的となる値を入れます。  
コンストラクタとして第一引数に有効な値、第二引数に有効でない値を入れます。これは後から`set_valid`関数でも可能です。  
`build`関数を呼び出します。

作っておいてなんですが、普通に二分探索を書いた方が速い気がします。

## 計算量
$$
O(logN)
$$

## 実装例

```cpp
#include<bits/stdc++.h>
using namespace std;

// bool is_valid(T mid, T target)
template <class T,bool (*is_valid)(T, T)>
struct BinarySearch{
  T valid_;
  T invalid_;
  BinarySearch(){}
  BinarySearch(T v,T iv):valid_(v),invalid_(iv){}

  void set_valid(T v,T iv){
    valid_=v;
    invalid_=iv;
  }

  T build(T target){
    auto valid=valid_;
    auto invalid=invalid_;

    while(abs(invalid-valid)>1){
      auto mid = (valid + invalid) / 2;
      if (is_valid(mid,target)) valid = mid;
      else invalid = mid;
    }
    return valid;
  }
};

vector<int> s;

bool is_valid(int m,int t){
  return s[m]<=t;
}

// AOJ_ALDS1_4_B
int main(){
  int n;
  cin>>n;
  s.resize(n);
  for(int i=0;i<n;i++) cin>>s[i];
  int q;
  cin>>q;
  int ans=0;
  BinarySearch<int,is_valid> bs(-1,n);
  for(int i=0;i<q;i++){
    int t;
    cin>>t;
    int idx=bs.build(t);
    ans+=(s[idx]==t);
  }
  cout<<ans<<endl;
}
```

---
title: Substring
description: 文字列 連続部分文字列
date: 2021/04/07
---

## 説明

## 計算量

## 実装例

```cpp
#include <bits/stdc++.h>
using namespace std;

string substr(string &s,int l,int r,bool rflg=false){
  string res="";
  if(rflg) for(int i=r-1;i>=l;i--) res+=s[i];
  else for(int i=l;i<r;i++) res+=s[i];
  return res;
}

int main(){
  string s;
  cin>>s;
  cout<<substr(s,1,s.size()-1)<<endl;
  cout<<substr(s,1,s.size()-1,true)<<endl;
}
```

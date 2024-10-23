---
title: OiClass PU2TI 327 嘤嘤的珂朵莉树题解
date: 2024-10-21 21:00:00
categories:
- Solution
---

### 题意

$n - 1$ 条主边构成一棵树，再在上面加 $m$ 条辅边，对这颗树进行若干次操作，每次操作有参数 $opt, u, k$，
若 $opt = 1$，则将点 $u$ 权值加 $k$，并对所有通过主边或辅边与 $u$ 相邻且深度比 $u$ 小的点重复此操作。
若 $opt = 2$，则将点 $u$ 权值加 $k$，并对所有通过主边或辅边与 $u$ 相邻且深度比 $u$ 大的点重复此操作。

求最后所有点的权值。

<!--more-->

### 解法

观察到操作一不会影响任何深度比该点大的点，操作二不会影响任何深度比该点小的点，考虑离线处理，对于操作一，从下往上操作，对于操作二，从上往下操作。

Code:

```cpp
#include <bits/stdc++.h>

#define int long long

using namespace std;

const int N = 1e5 + 10, MOD = 1e9 + 7;

int n, m, q;
vector<int> g[N];
int tag1[N], tag2[N], dep[N], ans[N];
pair<int, int> a[N], b[N];

void dfs(int, int);

signed main()
{
  freopen("kdl.in", "r", stdin);
  freopen("kdl.out", "w", stdout);
  ios::sync_with_stdio(0);
  cin.tie(nullptr); cout.tie(nullptr);
  cin >> n >> m >> q;
  for (int i = 1; i <= n; i++)
    cin >> ans[i];
  for (int i = 1; i < n; i++)
  {
    int u, v;
    cin >> u >> v;
    g[u].push_back(v);
    g[v].push_back(u);
  }
  dfs(1, 0);
  for (int i = 1; i <= n; i++)
    a[i] = b[i] = make_pair(dep[i], i);
  sort(a + 1, a + n + 1);
  sort(b + 1, b + n + 1, greater<pair<int, int>>());
  for (int i = 1; i <= m; i++)
  {
    int u, v;
    cin >> u >> v;
    g[u].push_back(v);
    g[v].push_back(u);
  }
  while(q--)
  {
    int opt, u, k;
    cin >> opt >> u >> k;
    if (opt == 1)
    {
      tag1[u] += k;
      tag1[u] %= MOD;
    }
    else
    {
      tag2[u] += k;
      tag2[u] %= MOD;
    }
  }
  for (int i = 1; i <= n; i++)
  {
    ans[a[i].second] += tag2[a[i].second];
    ans[a[i].second] %= MOD;
    for (auto v : g[a[i].second])
    {
      if(dep[v] > a[i].first)
      {
        tag2[v] += tag2[a[i].second];
        tag2[v] %= MOD;
      }
    }
    ans[b[i].second] += tag1[b[i].second];
    ans[b[i].second] %= MOD;
    for (auto v : g[b[i].second])
    {
      if (dep[v] < b[i].first)
      {
        tag1[v] += tag1[b[i].second];
        tag1[v] %= MOD;
      }
    }
  }
  for (int i = 1; i <= n; i++)
    cout << ans[i] << ' ';
  exit(EXIT_SUCCESS);
}

void dfs(int u, int fa)
{
  for (auto v : g[u])
  {
    if (v != fa)
    {
      dep[v] = dep[u] + 1;
      dfs(v, u);
    }
  }
}
```

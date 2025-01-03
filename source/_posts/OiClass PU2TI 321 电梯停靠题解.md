---
title: OiClass PU2TI 321 电梯停靠题解
date: 2024-10-21 21:30:00
categories:
- 题解
---

### 题意
在范围 $\left [1, n \right ]$ 的数轴上，给定 $m$ 个子区间 $\left [l_i, r_i \right ]$，我们可以选择一个出发点 $x$，则贡献为 $\Sigma_{i = 1}^m \max(\left | l_i - x \right | ,\left | r_i - x \right |)$。求最小的贡献和其对应的 $x$，若 $x$ 有多个，输出最小的一个。

### 解法
假设我们有一个子区间 $\left [3, 5 \right ]$，则它对 $\forall x, x \in \left [ 1, n \right]$ 的贡献为：

| 下标 | 1 | 2 | 3 | 4 | 5 | 6 |
| -----------: | -----------: | -----------: | -----------: | -----------: | -----------: | -----------: |
| 贡献 | 10 | 8 | 6 | 6 | 6 | 8 |

<!--more-->

做个差分就是

|下标|1|2|3|4|5|6|
| -----------: | -----------: | -----------: | -----------: | -----------: | -----------: |-----------: |
|$c$ |10 | -2 | -2 | 0 | 0 | 2 |

这样还是有点不方便，那就再差分

|下标|1|2|3|4|5|6|
| -----------: | -----------: | -----------: | -----------: | -----------: | -----------: |-----------: |
|$c$| 10 | -12 | 0 | 2 | 0 | 2 |

这个差分数组记作 $c$。

这样每一个子区间我们只需要修改 $c_1,c_2,c_{l+1},c_{r+1}$ 就行了，十分的简单。
记得 $l = 1$ 时要特殊处理。

Code:

```cpp
#include <bits/stdc++.h>

#define int long long

using namespace std;

const int N = 5e5 + 10;

int n, m, minn = 1;
int a[N], b[N], s[N];

signed main()
{
  freopen("lift.in", "r", stdin);
  freopen("lift.out", "w", stdout);
  
  cin >> n >> m;
  for (int i = 1; i <= m; i++)
  {
    cin >> a[i] >> b[i];
    s[1] += (b[i] - a[i]) * 2 + (a[i] - 1) * 2;
    if (a[i] > 1)
    {
      s[2] += -(b[i] - a[i]) * 2 - (a[i] - 1) * 2 - 2;
      s[a[i] + 1] += 2;
    }
    else
      s[2] += -(b[i] - a[i]) * 2 - (a[i] - 1) * 2;
    s[b[i] + 1] += 2;
  }
  for (int i = 1; i <= n; i++)
  {
    s[i] += s[i - 1];
  }
  for (int i = 1; i <= n; i++)
  {
    s[i] += s[i - 1];
    if (s[minn] > s[i])
      minn = i;
  }
  cout << minn << ' ' << s[minn] << endl;
  exit(EXIT_SUCCESS);
}
```

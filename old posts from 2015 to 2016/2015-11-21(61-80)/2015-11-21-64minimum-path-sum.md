---
layout: post
title: "64.Minimum Path Sum"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

经典的动态规划题

{% highlight cpp %}

int minPathSum(vector<vector<int>>& grid) {
  int m = grid.size();
  int n = m == 0 ? 0 : grid[0].size();
  if (!m || !n) return 0;

  vector <vector <int> > f(m, vector <int>(n, INT_MAX));
  f[0][0] = grid[0][0];

  for (int i = 0; i < m; i++) {
    for (int j = 0; j < n; j++) {
      if (i) f[i][j] = min(f[i][j], f[i-1][j] + grid[i][j]);
      if (j) f[i][j] = min(f[i][j], f[i][j-1] + grid[i][j]);
    }
  }

  return f[m-1][n-1];
}

{% endhighlight %}
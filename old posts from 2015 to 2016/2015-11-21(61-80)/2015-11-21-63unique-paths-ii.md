---
layout: post
title: "63.Unique Paths II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

和上一条题目一样

{% highlight cpp %}

int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
  int m = obstacleGrid.size();
  int n = m == 0 ? 0 : obstacleGrid[0].size();
  if (!m || !n) return 0;

  vector <vector <int> > f(m, vector <int>(n, 0));
  f[0][0] = !obstacleGrid[0][0];
  for (int i = 0; i < m; i++) {
    for (int j = 0; j < n; j++) {
      if (obstacleGrid[i][j]) continue;
      if (i) f[i][j] += f[i-1][j];
      if (j) f[i][j] += f[i][j-1];
    }
  }

  return f[m-1][n-1];
}

{% endhighlight %}
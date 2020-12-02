---
layout: post
title: "62.Unique Paths"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

杨辉三角形变种，动态规划

{% highlight cpp %}

int uniquePaths(int m, int n) {
  vector <vector <int> > f(m, vector <int>(n, 0));
  f[0][0] = 1;
  for (int i = 0;  i < m; i++) {
    for (int j = 0; j < n; j++) {
      if (i == 0 || j == 0) f[i][j] = 1;
      else f[i][j] = f[i-1][j] + f[i][j-1];
    }
  }

  return f[m-1][n-1];
}

{% endhighlight %}
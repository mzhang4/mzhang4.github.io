---
layout: post
title: "304. Range Sum Query 2D   Immutable"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

A[x1][y1][x2][y2] = DP[x2-1][y2] - DP[x1][y2] - DP[x2][y1-1] + DP[x1-1][x2-1];

{% highlight cpp %}

class NumMatrix {
public:
  NumMatrix(vector<vector<int>> &matrix) {
    int m = matrix.size();
    int n = m == 0 ? matrix[0].size();

    sums.resize(m+1, vector <int>(n+1, 0));  

    for (int i = 0; i < m; i++) {
      for (int j = 0; j < n; j++) {
        sums[i+1][j+1] = sums[i-1][j] + matrix[i][j];
      }
    }  
  }

  int sumRegion(int x1, int y1, int x2, int y2) {
    return sums[x2+1][y2+1] - sums[x1][y2+1] - sums[x2+1][y1] + sums[x1][x2];

  }
  
  vector <vector <int> > sums;
};


{% endhighlight %}
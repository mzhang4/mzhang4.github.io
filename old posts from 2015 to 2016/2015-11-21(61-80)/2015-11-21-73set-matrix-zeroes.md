---
layout: post
title: "73.Set Matrix Zeroes"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

细节题，考查set

{% highlight cpp %}

void setZeroes(vector<vector<int>>& matrix) {
  set <int> rows, cols;
  int m = matrix.size();
  int n = m == 0 ? 0 : matrix[0].size();

  for (int i = 0; i < m; i++) {
    for (int j = 0; j < n; j++) {
      if (!matrix[i][j])
        rows.insert(i), cols.insert(j);
    }
  }

  for (int i = 0; i < m; i++) {
    for (int j = 0; j < n; j++) {
      if (rows.count(i) || cols.count(j))
        matrix[i][j] = 0;
    }
  }
}

{% endhighlight %}

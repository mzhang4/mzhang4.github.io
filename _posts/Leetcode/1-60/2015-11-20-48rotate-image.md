---
layout: post
title: "48.Rotate Image"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

细节实现题，一圈一圈对image进行90度的rotate

{% highlight cpp %}

void rotate(vector<vector<int>>& matrix) {
  int n = matrix.size();
  for (int layer = 0; layer < n/2; layer++) {
    int offset = layer;
    for (int i = layer; i < n-layer-1; i++) {
      int tmp = matrix[layer][i];
      matrix[layer][i] = matrix[n-i-1][layer];
      matrix[n-i-1][layer] = matrix[n-layer-1][n-1-i];
      matrix[n-layer-1][n-1-i] = matrix[i][n-layer-1];
      matrix[i][n-layer-1] = tmp;
    }
  }
}

{% endhighlight %}
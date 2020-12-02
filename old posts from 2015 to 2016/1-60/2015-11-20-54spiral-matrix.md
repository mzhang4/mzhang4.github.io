---
layout: post
title: "54.Spiral Matrix"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

细节实现题，分别用4个坐标表示上下左右应该访问到的点，然后进行用循环遍历数组

{% highlight cpp %}
vector<int> spiralOrder(vector<vector<int>>& matrix) {
  if (matrix.size() == 0) return vector <int>();
  int ur = 0, uc = 0, dr = matrix.size(), dc = matrix[0].size();
  int r = 0, c = 0;
  vector <int> ans;
  while(true) {
    while (c<dc) ans.push_back(matrix[r][c++]);
    c--; r++; ur++; if (dr<=ur) break;
    while (r<dr) ans.push_back(matrix[r++][c]);
    r--; c--; dc--; if (dc<=uc) break;
    while (c>=uc) ans.push_back(matrix[r][c--]);
    c++; r--; dr--; if (dr<=ur) break;
    while (r>=ur) ans.push_back(matrix[r--][c]);
    r++; c++; uc++; if (dc <= uc) break;
  }
  return ans;
}
{% endhighlight %}
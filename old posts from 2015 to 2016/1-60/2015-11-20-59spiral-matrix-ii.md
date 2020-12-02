---
layout: post
title: "59.Spiral Matrix II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

比上一条简单，for循环求解即可。细节实现题

{% highlight cpp %}

vector<vector<int>> generateMatrix(int n) {
  if (n==0) return vector<vector<int>>();
  vector <vector <int> > ans(n, vector <int>(n, 0));
  int r = 0, c = 0;
  int cnt = 1;
  while (true) {
    while(c<n&&!ans[r][c]) { ans[r][c]=cnt++; c++; }
    c--; r++; if (cnt > n*n) break;
    while (r<n&&!ans[r][c]) {ans[r][c]=cnt++; r++; }
    r--; c--; if (cnt > n*n) break;
    while (c>=0&&!ans[r][c]) { ans[r][c]=cnt++; c--; }
    c++; r--; if (cnt > n*n) break;
    while (r>=0&&!ans[r][c]) { ans[r][c]=cnt++; r--; }
    r++; c++; if (cnt > n*n) break;
  }
  return ans;
}

{% endhighlight %}

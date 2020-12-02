---
layout: post
title: "118.Pascal's Triangle"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

dynamic programming

{% highlight cpp %}

vector<vector<int>> generate(int numRows) {
  vector <vector <int> > ans;
  if (!numRows) return ans;

  for (int i = 1; i <= numRows; i++) {
    ans.push_back(vector<int>(i, 0));
    if (i == 1) ans[0][0] = 1;
    else {
      for (int j = 0; j < i; j++) {
        if (j < i-1) ans[i-1][j] += ans[i-2][j];
        if (j-1>=0) ans[i-1][j] += ans[i-2][j-1];
      }
    }
  }

  return ans;
}


{% endhighlight %}
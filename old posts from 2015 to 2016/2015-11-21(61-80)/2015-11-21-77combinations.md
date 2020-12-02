---
layout: post
title: "77.Combinations"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

dfs

{% highlight cpp %}

vector<vector<int>> combine(int n, int k) {
  vector <vector <int>> ans;
  dfs(ans, vector<int>(), 1, 0, n, k);
  return ans;   
}

void dfs(vector <vector <int>>& ans, vector <int> cur, int start, int step, int n, int k) {
  if (step == k) {
    ans.push_back(cur);
    return;
  }

  if (start > n) return;

  dfs(ans, cur, start + 1, step, n, k);
  cur.push_back(start);
  dfs(ans, cur, start + 1, step+1, n, k);
}

{% endhighlight %}

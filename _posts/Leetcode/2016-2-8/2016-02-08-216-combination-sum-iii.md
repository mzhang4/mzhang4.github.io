---
layout: post
title: "216. Combination Sum III"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

dfs

{% highlight cpp %}
class Solution {
public:
  vector<vector<int>> combinationSum3(int k, int n) {
    vector <vector <int>> ans;
    dfs(ans, vector<int>(), 1, k, n);
    return ans;
  }
  
  void dfs(vector<vector <int>>& ans, vector <int> cur, int start, int k, int n) {
    if (k == 0 && n == 0) {
      ans.push_back(cur);
      return;
    }
    
    for (int i = start; i <= 9; i++) {
      if (i > n) break;
      cur.push_back(i);
      dfs(ans, cur, i+1, k-1, n-i);
      cur.pop_back();
    }
  }
};

{% endhighlight %}
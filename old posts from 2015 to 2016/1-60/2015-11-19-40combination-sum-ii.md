---
layout: post
title: "40.Combination Sum II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

同上一题一样，dfs即可，注意和上一题不同的地方，相当于一个是求不同的子集，
一个是求全排列（虽然上一个结果并不包含所有元素）

{% highlight cpp %}

vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
  sort(candidates.begin(), candidates.end());
  vector <vector <int> > ans;
  dfs(ans, vector <int>(), 0, 0, candidates, target);
  return ans;
}

void dfs(vector <vector <int> >& ans, vector <int> cur, int sum, int step,
        vector <int>& candidates, int target) {
  if (sum == target) ans.push_back(cur);
  
  if (step == candidates.size()) {
    return;
  }          
  
  if (sum > target) return;
  
  for (int i = step; i < candidates.size(); i++) {
    if (i != step && candidates[i] == candidates[i - 1]) continue;
    cur.push_back(candidates[i]);
    dfs(ans, cur, sum + candidates[i], i+1, candidates, target);
    cur.pop_back();
  }
}

{% endhighlight %}
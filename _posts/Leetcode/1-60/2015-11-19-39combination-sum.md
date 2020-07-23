---
layout: post
title: "39.Combination Sum"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

标准的bruteforce类题，dfs解决即可，注意剪纸和去重

{% highlight cpp %}
vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
  vector <vector <int> > ans;
  sort(candidates.begin(), candidates.end());
  candidates.erase(unique(candidates.begin(), candidates.end()), candidates.end());
  dfs(ans, vector <int>(), 0, 0, candidates, target);
  return ans;
}

void dfs(vector <vector <int> >& ans, vector <int> cur, int sum, int step, 
        vector <int>& candidates, int target) {
  if (step == candidates.size()) {
    if (sum == target) ans.push_back(cur);
    return;
  }
  if (sum > target) return;
    
  cur.push_back(candidates[step]);
  dfs(ans, cur, sum + candidates[step], step, candidates, target);
  cur.pop_back();
  dfs(ans, cur, sum, step + 1, candidates, target);
}
{% endhighlight %}
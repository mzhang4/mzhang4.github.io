---
layout: post
title: "47.Permutations II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

dfs生成全排列，和上一条的不同是这里需要去重

{% highlight cpp %}

vector<vector<int>> permuteUnique(vector<int>& nums) {
  map <int, int> dict;
  for (auto n : nums) dict[n]++;
  vector <vector <int> > ans;
  dfs(ans, vector <int>(), dict, (int)nums.size());
  return ans; 
}

void dfs(vector <vector <int> >& ans, vector <int> cur, map <int, int>& dict, int n) {
  if (cur.size() == n) {
    ans.push_back(cur);
    return;
  }

  for (auto it = dict.begin(); it != dict.end(); ++it) {
    if (it->second == 0) continue;
    it->second--;
    cur.push_back(it->first);
    dfs(ans, cur, dict, n);
    cur.pop_back();
    it->second++;
  }
}

{% endhighlight %}
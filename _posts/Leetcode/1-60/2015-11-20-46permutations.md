---
layout: post
title: "46.Permutations"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

dfs生成全排列

{% highlight cpp %}

vector<vector<int>> permute(vector<int>& nums) {
  vector <vector <int> > ans;
  int n = nums.size();
  vector <bool> vis(n, false);
  dfs(ans, vector <int>(), vis, nums);
  return ans;    
}

void dfs(vector <vector <int> >& ans, vector <int> cur, vector <bool> vis, 
        vector <int>& nums) {
  if (cur.size() == nums.size()) {
    ans.push_back(cur);
    return;
  }

  for (int i = 0; i < nums.size(); i++) {
    if (vis[i]) continue;
    vis[i] = true;
    cur.push_back(nums[i]);
    dfs(ans, cur, vis, nums);
    cur.pop_back();
    vis[i] = false;
  }
}

{% endhighlight %}
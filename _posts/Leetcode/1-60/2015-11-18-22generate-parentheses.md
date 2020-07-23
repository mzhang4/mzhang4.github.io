---
layout: post
title: "22.Generate Parentheses"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

搜索类问题，dfs

{% highlight cpp %}

vector<string> generateParenthesis(int n) {
  vector <string> ans;
  dfs(ans, "", 0, 0, n);
  return ans;    
}

void dfs(vector <string>& ans, string cur, int l, int r, int n) {
  if (r > l || l > n) return;
  if (r == n) {
    ans.push_back(cur);
    return;
  }

  dfs(ans, cur + '(', l+1, r, n);
  dfs(ans, cur + ')', l, r + 1, n);
}

{% endhighlight %}
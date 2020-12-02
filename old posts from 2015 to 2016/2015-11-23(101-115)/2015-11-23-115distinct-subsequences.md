---
layout: post
title: "115.Distinct Subsequences"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

记忆化搜索

{% highlight cpp %}

string s, t;
vector <vector <int> > dp;

int numDistinct(string s, string t) {
  int m = s.length(), n = t.length();
  if (!m || !n) return 0;

  this->s = s;
  this->t = t;
  dp.resize(m, vector<int>(n, -1));
  return go(0, 0);
}

int go(int x, int y) {
  if (y == t.length()) return 1;
  if (x == s.length()) return 0;

  int& ans = dp[x][y];
  if (ans != -1) return ans;
  
  ans = 0;
  if (s[x] == t[y]) {
    ans += go(x+1, y+1);
  }
  ans += go(x+1, y);
  return ans;
}

{% endhighlight %}
---
layout: post
title: "10.Regular Expression Matching"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

记忆化搜索
直接进行迭代，不用dp保存中间结果也不回超时

{% highlight cpp %}

vector <vector <int> > dp;
int m, n;
string s, p;
bool isMatch(string s, string p) {
  this->s = s;
  this->p = p;

  m = s.length();
  n = p.length();

  dp.resize(m, vector <int>(n, -1));
  return go(0, 0);    
}

int go(int x, int y) {
  if (x == m && y != n) return 0;
  if (x != m && y == n) return 0;
  if (x == m && y == n) return 1;

  int& ans = dp[x][y];
  if (ans != -1) return true;

  if (s[x] == p[y] || p[y] == '.')
    return go(x+1, y+1);
  else if (p[y] == '*' || (s[x] == p[y-1] || p[y-1] == '.'))
    ans = go(x+1, y+1) | go(x+1, y);
  else if (p[y] == '*')
    ans = go(x, y+1);

  return ans;
}

{% endhighlight %}
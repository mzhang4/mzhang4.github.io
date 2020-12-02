---
layout: post
title: "96.Unique Binary Search Trees"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

记忆化搜索
{% highlight cpp %}

vector <int> f;

int numTrees(int n) {
  f.resize(n+1, -1);
  f[0] = 1;
  return go(n); 
}

int go(int n) {
  int& ans = f[n];
  if (ans != -1) return ans;

  ans = 0;
  for (int i = 0; i <= n-1; i++) {
    ans += go(i) * go(n-i-1);
  }

  return ans;
}

{% endhighlight %}
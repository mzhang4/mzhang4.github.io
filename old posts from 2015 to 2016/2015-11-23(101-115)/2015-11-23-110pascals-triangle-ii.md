---
layout: post
title: "110.Pascal's Triangle II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

和第一条一样 简单的动归题

{% highlight cpp %}

vector<int> getRow(int n) {
  vector <int> cur;
  vector <int> prev(1, 1);

  for (int i = 1; i <= n; i++) {
    cur.resize(i+1, 0);
    for (int j = 0; j <= i; j++) {
      if (j-1>=0) cur[j] += prev[j-1];
      if (j <= i-1) cur[j] += prev[j];
    }
    swap(cur, prev);
    cur.clear();
  }

  return prev;
}

{% endhighlight %}
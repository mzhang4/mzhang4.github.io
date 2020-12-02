---
layout: post
title: "70.Climbing Stairs"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

简单的动态规划题

{% highlight cpp %}

int climbStairs(int n) {
  if (!n) return 0;

  vector <int> f(n+1, 0);
  f[0] = 1;

  for (int i = 1; i <= n; i++) {
  	f[i] = f[i-1];
  	if (i-2>=0) f[i] += f[i-2];
	}

	return f[n];
}

{% endhighlight %}
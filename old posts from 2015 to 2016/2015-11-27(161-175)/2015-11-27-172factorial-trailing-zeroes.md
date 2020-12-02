---
layout: post
title: "172.Factorial Trailing Zeroes"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

计算n里面每一个数有多少个约数5

{% highlight cpp %}
int trailingZeroes(int n) {
  int ans = 0;
  while (n) {
    ans += n/5;
    n /= 5;
  }
  return ans;
}
{% endhighlight %}
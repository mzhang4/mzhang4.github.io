---
layout: post
title: "319. Bulb Switcher"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

run brute force first and find the pattern
because when n is a perfect square number, then it will be on at last.

{% highlight cpp %}

class Solution {
public:
  int bulbSwitch(int n) {
    return sqrt(n);
  }
};

{% endhighlight %}
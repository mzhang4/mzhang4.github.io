---
layout: post
title: "136.Single Number"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

位操作

{% highlight cpp %}

int singleNumber(vector<int>& nums) {
  int ans = 0;
  for (auto n : nums) {
    ans ^= n;
  }   
  return ans;
}

{% endhighlight %}
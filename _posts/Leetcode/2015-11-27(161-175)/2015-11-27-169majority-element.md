---
layout: post
title: "169.Majority Element"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

voting algorithm

{% highlight cpp %}

int majorityElement(vector<int>& nums) {
  int cnt = 1;
  int ans = 0;

  for (int i = 0; i < nums.size(); i++) {
    if (nums[i] == ans) cnt++;
    else cnt--;

    if (cnt <= 0) ans = nums[i], cnt = 1;
  }   

  return ans;
}

{% endhighlight %}
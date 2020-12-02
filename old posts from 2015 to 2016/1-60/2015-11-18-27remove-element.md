---
layout: post
title: "27.Remove Element"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

维护一个ind，当nums[i]!=val时，nums[ind++] = nums[i]

{% highlight cpp %}

int removeElement(vector<int>& nums, int val) {
  int ind = 0;
  for (int i = 0; i < nums.size(); i++) {
    if (nums[i] != val)
      nums[ind++] = nums[i];
  }    
  return ind;
}

{% endhighlight %}
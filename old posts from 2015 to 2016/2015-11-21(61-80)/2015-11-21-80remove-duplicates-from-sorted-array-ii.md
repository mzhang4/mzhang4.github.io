---
layout: post
title: "80.Remove Duplicates from Sorted Array II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

细节实现题

{% highlight cpp %}

int removeDuplicates(vector<int>& nums) {
  if (nums.size() < 3) return nums.size();
  int ind = 2;
  for (int i = 2; i < nums.size(); i++) {
    if (nums[i] != nums[ind-2])
      nums[ind++] = nums[i];
  }
  return ind;
}

{% endhighlight %}
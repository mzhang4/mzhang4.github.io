---
layout: post
title: "26.Remove Duplicates from Sorted Array"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

维护一个ind, 当nums[i]!=nums[ind]时，nums[++ind]=nums[i]

{% highlight cpp %}

int removeDuplicates(vector<int>& nums) {
  if (nums.size() < 1) return nums.size();
  int ind = 0;    

  for (int i = 1; i < nums.size(); i++) {
    if (nums[i] != nums[ind])
      nums[++ind] = nums[i];
  }

  return ind + 1;
}

{% endhighlight %}

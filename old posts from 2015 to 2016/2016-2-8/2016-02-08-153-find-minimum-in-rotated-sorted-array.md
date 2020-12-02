---
layout: post
title: "153. Find Minimum in Rotated Sorted Array"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

return the first true

{% highlight cpp %}

class Solution {
public:
  int findMin(vector<int>& nums) {
    int l = 0, h = nums.size() - 1;

    while (l < h) {
      int mid = l + (h - l)/2;
      if (nums[mid] <= nums.back()) {
        h = mid;
      } else {
        l = mid + 1;
      }
    }

    return nums[l];
  }
};

{% endhighlight %}
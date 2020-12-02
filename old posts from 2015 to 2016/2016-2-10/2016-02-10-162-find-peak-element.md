---
layout: post
title: "162. Find Peak Element"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

binary search

{% highlight cpp %}

class Solution {
public:
  int findPeakElement(vector<int>& nums) {
    int l = 0, h = nums.size() - 1;
    while (l < h) {
      int mid = l + (h-l) / 2;
      bool b1 = mid == 0 || nums[mid] > nums[mid-1];
      bool b2 = (mid == nums.size() - 1) || nums[mid] > nums[mid+1];
      if (b1 && b2) return mid;
      
      if (!b1) {
        h = mid-1;
      } else {
        l = mid+1;
      }
    }
    
    return l;
  }
};

{% endhighlight %}
---
layout: post
title: "154. Find Minimum in Rotated Sorted Array II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

binary search, 和上一条一样

{% highlight cpp %}

class Solution {
public:
  int findMin(vector<int>& nums) {
    int l = 0, h = nums.size()-1;
    while (l < h) {
      int mid = l + (h-l)/2;
      
      if (nums[mid]<nums[h]) {
        h = mid;    
      } else if (nums[mid] > nums[h]) {
        l = mid+1;
      } else {
        h--;
      }
    }
    
    return nums[l];
  }
};

{% endhighlight %}

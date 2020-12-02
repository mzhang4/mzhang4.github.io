---
layout: post
title: "33.Search in Rotated Sorted Array"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

二分法，注意对下界和上界的更新

{% highlight cpp %}

int search(vector<int>& nums, int target) {
  int l = 0, h = nums.size();
  while (h > l) {
    int mid = l + (h-l)/2;
    if (nums[mid] == target) return mid;
    
    if (nums[l] <= nums[mid]) {
      if (target >= nums[l] && target < nums[mid])
        h = mid;
      else
        l = mid+1;
    }
    else {
      if (target > nums[mid] && target <= nums[h-1])
        l = mid+1;
      else
        h = mid;
    }
  }
  return -1;
}

{% endhighlight %}

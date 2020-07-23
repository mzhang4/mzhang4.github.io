---
layout: post
title: "81. Search in Rotated Sorted Array II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

binary search， almost same as the first one.

{% highlight cpp %}

class Solution {
public:
  bool search(vector<int>& nums, int target) {
  	int l = 0, h = nums.size();
  	while (l < h) {
  		int mid = l+(h-l)/2;
  		if (nums[mid] == target) return true;

  		if (nums[l] < nums[mid]) {
  			if (nums[l] <= target && nums[mid] > target)
  				h = mid;
  			else
  				l = mid+1;
  		} else if (nums[l] > nums[mid]) {
  			if (nums[mid] < target && nums[h-1] >= target)
  				l = mid+1;
  			else
  				h = mid;
  		} else {
  			l++;
  		}
  	}
  	
  	return false;
  }
};

{% endhighlight %}
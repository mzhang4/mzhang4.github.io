---
layout: post
title: "34.Search for a Range"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

二分法实现lower_bound和upper_bound

std
{% highlight cpp %}
vector<int> searchRange(vector<int>& nums, int target) {
  int l = lower_bound(nums.begin(), nums.end(), target) - nums.begin();
  int r = upper_bound(nums.begin(), nums.end(), target) - nums.begin();
  if (nums[l] != target) return vector <int>({-1, -1});
  return vector <int>({l, r-1});
}
{% endhighlight %}

二分法: lower->第一个true, upper->最后一个false
{% highlight cpp %}
vector<int> searchRange(vector<int>& nums, int target) {
  int l = lowerBound(nums, target);
  int r = upperBound(nums, target);
  if (nums[l] != target) return vector <int>({-1, -1});
  return vector <int>({l, r});
}

int lowerBound(vector <int>& nums, int target) {
  int l = 0, h = nums.size();
  while (h > l) {
    int mid = l + (h-l)/2;
    if (nums[mid]>=target)
      h = mid;
    else
      l = mid+1;
  }
  return l;
}

int upperBound(vector <int>& nums, int target) {
  int l =0, h = nums.size();
  while (h > l) {
    int mid = l + (h-l+1)/2;
    if (nums[mid] > target)
      h = mid - 1;
    else
      l = mid; 
  }
  if (l==nums.size()) l--;
  return l;
}
{% endhighlight %}
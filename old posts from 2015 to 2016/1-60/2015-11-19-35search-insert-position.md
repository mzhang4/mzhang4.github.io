---
layout: post
title: "35.Search Insert Position"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

lower_bound 实现题，或者调用std::lower_bound() 或者用二分法实现

std::lower_bound()
{% highlight cpp %}
int searchInsert(vector<int>& nums, int target) {
  return lower_bound(nums.begin(), nums.end(), target) - nums.begin();
}
{% endhighlight%}

二分法(需要返回第一个true)

{% highlight cpp %}
int searchInsert(vector<int>& nums, int target) {
  return lowerBound(nums, target);
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

{% endhighlight %}


---
layout: post
title: "287. Find the Duplicate Number"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

bucket sort. Put all numbers in the correct place

{% highlight cpp %}

class Solution {
public:
  int findDuplicate(vector<int>& nums) {
    bucket_sort(nums);
    for (int i = 0; i < nums.size(); i++) {
      if (nums[i] != i + 1)
        return nums[i];
    }
  }

  void bucket_sort(vector <int>& nums) {
    for (int i = 0; i < nums.size(); i++) {
      while (nums[i] != i + 1 && nums[i] != nums[nums[i]-1]) {
        swap(nums[i], nums[nums[i]-1]);
      }
    }
  }
};

{% endhighlight %}


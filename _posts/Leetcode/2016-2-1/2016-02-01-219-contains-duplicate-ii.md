---
layout: post
title: "219. Contains Duplicate II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

go through numbers, record index each number occurs last time.
if a number is already recorded and calculate their distance

{% highlight cpp %}

class Solution {
public:
  bool containsNearbyDuplicate(vector<int>& nums, int k) {
    map <int, int> last;
    for (int i = 0; i < nums.size(); i++) {
      if (last.count(nums[i]) && i - last[nums[i]] <= k) {
        return true;
      }
      last[nums[i]] = i;
    }
    return false;
  }
};

{% endhighlight %}
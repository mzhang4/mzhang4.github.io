---
layout: post
title: "330. Patching Array"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

We keep what numbers are missing, the first 1 is one.
Then if there exists a number in the array which is smaller than missing, we can add to result and make the next missing number
to be nums[idx] + missing
If there is no such number in the array that nums[idx] <= missing, then we can add missing to the array.

{% highlight cpp %}

class Solution {
public:
  int minPatches(vector<int>& nums, int n) {
    int ans = 0, idx = 0;
    long long total = 1;
    long long nn = (long long)n;
    while (total <= n) {
      if (idx < nums.size() && nums[idx] <= total) {
        total += nums[idx++];
      } else {
        total <<= 1;
        ans++;
      }
    }
    return ans;
  }
};

{% endhighlight %}

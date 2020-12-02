---
layout: post
title: "334. Increasing Triplet Subsequence"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

dp. dp[0][i] = true, if there is a number smaller than nums[i] before
dp[1][i] = true, if there is a number greater than nums[i] after

{% highlight cpp %}

class Solution {
public:
  bool increasingTriplet(vector<int>& nums) {
    if (nums.size() < 3) return false;
    int n = nums.size();
    
    int dp[2][n];
    memset(dp, 0, sizeof(dp));
    int lo = nums[0], hi = nums[n-1];
    
    for (int i = 1; i < n; i++) {
      lo = min(nums[i], lo);
      hi = max(nums[n-i-1], hi);
      if (nums[i] > lo) dp[0][i] = 1;
      if (nums[n-i-1] < hi) dp[1][n-i-1] = 1;
    }
    
    for (int i = 0; i < n; i++) {
      if (dp[0][i] && dp[1][i])
        return true;
    }
    
    return false;
  }
};

{% endhighlight %}
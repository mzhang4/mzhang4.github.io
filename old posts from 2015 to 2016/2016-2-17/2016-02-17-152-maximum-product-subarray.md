---
layout: post
title: "152. Maximum Product Subarray"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

dp, dp[n][2], dp[n][0] denotes largest number ends with n,
dp[n][1] denotes smallest number ends with n

{% highlight cpp %}

class Solution {
public:
  int maxProduct(vector<int>& nums) {
    int n = nums.size();
    int ans = INT_MIN;
    vector <vector <int> > dp(n, vector <int>(2, 0));
      
    for (int i = 0; i < nums.size(); i++) {
      if (!i) dp[i][0] = dp[i][1] = nums[i];
      else {
        dp[i][0] = max(nums[i], max(dp[i-1][0] * nums[i], dp[i-1][1] * nums[i]));
        dp[i][1] = min(nums[i], min(dp[i-1][0] * nums[i], dp[i-1][1] * nums[i]));
      }

      ans = max(ans, dp[i][0]);
    }

    return ans;
  }
};

{% endhighlight %}
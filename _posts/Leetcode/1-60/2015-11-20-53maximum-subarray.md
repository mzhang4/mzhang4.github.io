---
layout: post
title: "53.Maximum Subarray"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

经典的dp题

{% highlight cpp %}

int maxSubArray(vector<int>& nums) {
  int n = nums.size();
  if (!n) return 0;
  vector <int> dp(n, 0);
  dp[0] = nums[0];
  int ans = nums[0];
  for (int i=1; i < n; i++) {
    dp[i] = nums[i] + max(dp[i-1], 0);
    ans = max(ans, dp[i]);
  }    
  return ans;
}

{% endhighlight %}
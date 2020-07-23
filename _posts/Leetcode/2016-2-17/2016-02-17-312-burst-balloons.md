---
layout: post
title: "312. Burst Balloons"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

dp, use f[i][j] to denote the result can get from i to j
so f[i][j] = f[i][k-1] + f[k+1][j] + nums[i-1]*nums[j+1]*nums[k];

{% highlight cpp %}

class Solution {
public:
  int maxCoins(vector<int>& nums) {
    int n = nums.size();
    nums.insert(nums.begin(), 1);
    nums.push_back(1);
    vector <vector <int> > dp(nums.size(), vector <int>(nums.size(), 0));
    
    for (int len = 1; len <= n; len++) {
      for (int l = 1; l + len -1 <= n; l++) {
        int r = l + len - 1;
        for (int k = l; k <= r; k++) {
          dp[l][r] = max(dp[l][r], dp[l][k-1] + dp[k+1][r] + nums[l-1]*nums[r+1]*nums[k]);
        }
      }
    }

    return dp[1][n];
  }
};

{% endhighlight %} 
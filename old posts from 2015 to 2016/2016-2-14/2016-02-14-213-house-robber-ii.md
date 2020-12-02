---
layout: post
title: "213. House Robber II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

分两种情况dp，第一个可以盗，第一个不可以盗

{% highlight cpp %}

class Solution {
public:
  int rob(vector<int>& nums) {
    int n = nums.size();
    if (!n) return 0;
    if (n == 1) return nums[0];
    
    int f[2][n];
    memset(f, 0, sizeof(f));
    f[0][0] = nums[0];
    f[1][1] = nums[1];
    int ans = max(f[0][0], f[1][1]);

    for (int i = 1; i < n-1; i++) {
        f[0][i] = nums[i];
      for (int j = 0; j < i-1; j++) {
        f[0][i] = max(f[0][j] + nums[i], f[0][i]);
      }
      ans = max(ans, f[0][i]);
    }

    for (int i = 2; i < n; i++) {
        f[1][i] = nums[i];
      for (int j = 0; j < i-1; j++) {
        f[1][i] = max(f[1][j] + nums[i], f[1][i]);
      }
      ans = max(ans, f[1][i]);
    }

    return ans;
  }
};

{% endhighlight %}
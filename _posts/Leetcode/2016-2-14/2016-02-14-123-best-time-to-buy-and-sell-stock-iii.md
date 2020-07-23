---
layout: post
title: "123. Best Time to Buy and Sell Stock III"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

dp, 因为可以做2次transaction，所以最大值为从0-i的最大值加上从i-n-1的最大值。
分别从两个方向去求这两个最大值即可。

{% highlight cpp %}

class Solution {
public:
  int maxProfit(vector<int>& prices) {
    int n = prices.size();
    if (!n) return 0;
    int dp[2][n];
    memset(dp, 0, sizeof(dp));
    
    int l = prices[0], h = prices[n-1];
    for (int i = 1; i < n; i++) {
      l = min(l, prices[i]);
      dp[0][i] = max(dp[0][i-1], prices[i]-l);
      h = max(h, prices[n-i-1]);
      dp[1][n-i-1] = max(dp[1][n-i], h-prices[n-i-1]);
    }
    
    int ans = 0;
    for (int i = 0; i < n; i++) {
      ans = max(ans, max(dp[0][i]+dp[1][i], max(dp[0][i], dp[1][i])));
    }
    
    return ans;
  }
};

{% endhighlight %}
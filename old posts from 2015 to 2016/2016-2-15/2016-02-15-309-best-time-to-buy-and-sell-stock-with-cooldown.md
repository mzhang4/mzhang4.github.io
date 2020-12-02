---
layout: post
title: "309. Best Time to Buy and Sell Stock with Cooldown"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

{% highlight cpp %}

class Solution {
public:
  int maxProfit(vector<int>& prices) {
    int n = prices.size();
    if (!n) return 0;
    int dp[n];
    memset(dp, 0, sizeof(dp));

    for (int i = n-1; i>=0; i--) {
      int m = prices[i];
      for (int j = i; j < n; j++) {
        m = min(m, prices[j]);
        dp[i] = max(dp[i], prices[j]-m+(j+2<n?dp[j+2] : 0));
      }
    }

    return dp[0];
  }
};

{% endhighlight %}

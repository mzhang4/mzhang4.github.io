---
layout: post
title: "188. Best Time to Buy and Sell Stock IV"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

local[i][k] = global[i-1][k] + p[i]-p[i-1], local[i-1][k-1] + max(diff, 0);
global[i][k] = max(local[i][k], global[i-1][k]);

{% highlight cpp %}


class Solution {
public:
  int maxProfit(int k, vector<int>& prices) {
    if (k >= prices.size()) return solve(prices); 
    int n = prices.size();
    if (n == 0) return 0;

    vector <vector <int> > local(n, vector <int>(k+1, 0));
    vector <vector <int> > global(n, vector <int>(k+1, 0));


    for (int i = 1; i < n; i++) {
      int diff = prices[i] - prices[i-1];
      for (int j = 1; j <= k; j++) {
        local[i][j] = max(global[i-1][j-1]+max(diff, 0), local[i-1][j]+diff);
        global[i][j] = max(local[i][j], global[i-1][j]);
      }
    }

    return global[n-1][k];
  } 

  int solve(vector <int>& prices) {
    int ans = 0;
    for (int i = 1; i < prices.size(); i++) {
      if (prices[i] > prices[i-1])
        ans += prices[i] - prices[i-1];
    }
    return ans;
  }
};

{% endhighlight %}
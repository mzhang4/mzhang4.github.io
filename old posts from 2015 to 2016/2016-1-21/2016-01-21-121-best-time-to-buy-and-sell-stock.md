---
layout: post
title: "121. Best Time to Buy and Sell Stock"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

as it is only allowed one trans, so for each day, calculate the min price before and calculate the profit if I sell the stock on that day.

{% highlight cpp %}

class Solution {
public:
  int maxProfit(vector<int>& prices) {
    if (prices.size() == 0) return 0;

    int ans = 0;
    int mp = prices[0];    
    for (int i = 0; i < prices.size(); i++) {
      mp = min(prices[i], mp);
      ans = max(ans, prices[i]-mp);
    }

    return ans;
  }
};

{% endhighlight %}
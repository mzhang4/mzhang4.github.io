---
layout: post
title: "122. Best Time to Buy and Sell Stock II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

as I can do as many transactions as possible, so this problem can be solved in greedy.
if p[i] > p[i-1], then it can generate profit and add to result

{% highlight cpp %}

class Solution {
public:
  int maxProfit(vector<int>& prices) {
    int ans = 0;
    for (int i = 1; i < prices.size(); i++) {
      ans += max(0, prices[i]-prices[i-1]);
    }      
    return ans;
  }
};

{% endhighlight %}
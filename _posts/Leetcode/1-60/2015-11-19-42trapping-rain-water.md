---
layout: post
title: "42.Trapping Rain Water"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

双向动规，从左到右，从右到左个一次，分别求出左边坐高的高度和右边最高的高度

{% highlight cpp %}

int trap(vector<int>& height) {
  int n = height.size();
  int dp[2][n];
  memset(dp, 0, sizeof(dp));
  if (!n) return 0;
  
  dp[0][0] = height[0];
  dp[1][n-1] = height[n-1]; 

  for (int i = 1; i < n; i++) {
    dp[0][i] = max(dp[0][i-1], height[i-1]);
    dp[1][n-i-1] = max(dp[1][n-i], height[n-i]);
  }

  int ans = 0;
  for (int i = 0; i < n; i++) {
    ans += max(0, min(dp[0][i], dp[1][i])-height[i]);
  }
  return ans;
}

{% endhighlight %}

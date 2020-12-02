---
layout: post
title: "300. Longest Increasing Subsequence"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

DP

{% highlight cpp %}

class Solution {
public:
  int lengthOfLIS(vector<int>& nums) {
    int n = nums.size();
    vector <int> f(n, 0);
    int ans = 0;
    for (int i = 0; i < n; i++) {
      f[i] = 1;
      if (i != n) {
        for (int j = 0; j < i; j++) {
          if (nums[i] > nums[j] && f[i] < f[j]+1)
            f[i] = f[j]+1;
        }
      }
      ans = max(ans, f[i]);
    }
    return ans;
  }
};

{% endhighlight %}

O(nlogn) 算法欠费

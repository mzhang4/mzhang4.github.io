---
layout: post
title: "238. Product of Array Except Self"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

dynamic programming

{% highlight cpp %}

class Solution {
public:
  vector<int> productExceptSelf(vector<int>& nums) {
    int n = nums.size();
    
    vector <int> res(n, 1);
    for (int i = n-2; i >= 0; i--) {
      res[i] = res[i+1]*nums[i+1];
    }

    int p = 1;
    for (int i = 0; i < n; i++) {
      res[i] *= p;
      p *= nums[i];
    }

    return res;
  }
};

{% endhighlight %}
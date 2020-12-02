---
layout: post
title: "325. Maximum Size Subarray Sum Equals k"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

最简单的方法应该是brute force， O(n^2）
但是题目中要求的是O(n)的算法，很容易想到的就是sliding window, 发现sliding window解决不了问题
之后想到的便是对于m~n的subarray他应该是 sum(0..n) - sum(0..m-1)，所以只需要用一个hashmap前面的值即可

{% highlight cpp %}

int maxSubArrayLen(vector<int>& nums, int k) {
  map <int, int> idx;
  idx[0] = 0;
  int s = 0, ans = 0;

  for (int i = 0; i < nums.size(); i++) {
    s += nums[i];
    if (idx.count(s-k)) {
      ans = max(ans, i+1-idx[s-k]);
    }
    
    if (!idx.count(s))
      idx[s] = i+1;
 }

  return ans;
}

{% endhighlight %}
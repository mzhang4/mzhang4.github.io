---
layout: post
title: "137. Single Number II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

分别用三个数去存储某一位出现了1次，2次和3次，对于每个数进行遍历，并更新这3个数

{% highlight cpp %}

class Solution {
public:
  int singleNumber(vector<int>& nums) {
    int one = 0, two = 0, three = 0;
    for (int i = 0; i < nums.size(); i++) {
      two |= nums[i] & one;
      one ^= nums[i];
      three = one&two;
      one &= ~three;
      two &= ~three;
    }    

    return one;
  }
};

{% endhighlight %}
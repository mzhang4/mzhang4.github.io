---
layout: post
title: "260. Single Number III"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

假设两个唯一出现一次的数为a和b，则求出c=a^b,找到c里面为1的最低位，那么必然有a的这一位为1或者b的这一位为1，
但是不可能同时出现a和b的这一位都为1，这样就可以将a和b区分出来

{% highlight cpp %}

class Solution {
public:
  vector<int> singleNumber(vector<int>& nums) {
    int sum = 0; int step = 0;
    vector <int> ans(2, 0);
    
    for (int i = 0; i < nums.size(); i++) {
      sum ^= nums[i];
    }
    
    while (!(sum&0x1)) { sum >>= 1; step++; }
    
    for (int i = 0; i < nums.size(); i++) {
      if (nums[i] & (1<<step)) {
        ans[0] ^= nums[i];
      } else {
        ans[1] ^= nums[i];
      }
    }
    
    return ans;
  }
};

{% endhighlight %}
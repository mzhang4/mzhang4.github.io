---
layout: post
title: "229. Majority Element II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

voting algorithm

{% highlight cpp %}

class Solution {
public:
  vector<int> majorityElement(vector<int>& nums) {
    int a = 0, b = 0;
    int num1 = 0, num2 = 0;
    
    for (int i = 0; i < nums.size(); i++) {
      if (nums[i] == num1) a++;
      else if (nums[i] == num2) b++;
      else {
        if (a == 0) {a =1 ; num1 = nums[i]; }
        else if (b == 0) { b= 1; num2 = nums[i]; }
        else {
          a--;
          b--;
        }
      }
    }
    
    vector <int> ans;
    if (ok(num1, nums)) ans.push_back(num1);
    if (num1 != num2 && ok(num2, nums)) ans.push_back(num2);
    
    return ans;
  }
    
  bool ok(int num, vector <int>& nums) {
    int cnt = 0;
    for (int i = 0; i < nums.size(); i++) {
      if (nums[i] == num)
          cnt++;
    }
    
    return cnt > 0 && cnt > nums.size() / 3;
  }
};

{% endhighlight %}

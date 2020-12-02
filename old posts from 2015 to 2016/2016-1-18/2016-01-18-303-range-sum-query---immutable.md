---
layout: post
title: "303. Range Sum Query   Immutable"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

{% highlight cpp %}

class NumArray {
public:
  NumArray(vector<int> &nums) {
    int n = nums.size();
    s.resize(n+1, 0);
    int sum = 0;
    for (int i = 0; i < n; i++) {
        sum += nums[i];
        s[i+1] = sum;
    }
  }

  int sumRange(int i, int j) {
    return s[j+1] - s[i];
  }
  
  vector <int> s;
};

{% endhighlight %}

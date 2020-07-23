---
layout: post
title: "307. Range Sum Query   Mutable"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}


RMQ或者BIT. BIT更好，代码长度更短，更容易写，并且空间复杂度低

{% highlight cpp %}

class NumArray {
public:
  NumArray(vector<int> &nums) {
    this->nums = nums;
    tree.resize(nums.size()+1, 0);
    for (int i = 0; i < nums.size(); i++) {
      add(i+1, nums[i]);
    }
  }

  void update(int i, int val) {
    int u = val - nums[i];
    nums[i] = val;
    add(i+1, u);
  }

  int sumRange(int i, int j) {
    return read(j+1) - read(i);
  }
  
  void add(int idx, int val) {
    while (idx < tree.size()) {
      tree[idx] += val;
      idx += (idx & -idx);
    }
  }
  
  int read(int idx) {
    int sum = 0;
    while (idx > 0) {
      sum += tree[idx];
      idx -= (idx & -idx);
    }
    return sum;
  }

  vector <int> nums;
  vector <int> tree;
};

{% endhighlight %}
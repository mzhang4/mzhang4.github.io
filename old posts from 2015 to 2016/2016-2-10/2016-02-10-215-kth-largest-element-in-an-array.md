---
layout: post
title: "215. Kth Largest Element in an Array"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

用quicksort里面的partition, 如果partition得到的数的index和k一样，则返回
否则recursive call

{% highlight cpp %}

class Solution {
public:
  int findKthLargest(vector<int>& nums, int k) {
    int ind = partition(nums);
    if (ind+1 == k) return nums[ind];
    if (ind+1 > k) {
      nums = vector <int>(nums.begin(), nums.begin()+ind);
      return findKthLargest(nums, k);
    }
    else {
      nums = vector <int>(nums.begin()+ind+1, nums.end());
      return findKthLargest(nums, k-ind-1);
    }
  }

  int partition(vector <int>& nums) {
    int pivot = nums[0];
    int ind = 0;
    for (int i = 1; i < nums.size(); i++) {
      if (nums[i] > pivot) {
        swap(nums[i], nums[++ind]);
      }
    }

    swap(nums[ind], nums[0]);
    return ind;
  }
};


{% endhighlight %}
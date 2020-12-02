---
layout: post
title: "31.Next Permutation"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

std::next_permutation()

{% highlight cpp %}

void nextPermutation(vector<int>& nums) {
  if (next_permutation(nums.begin(), nums.end()))
    return;
  reverse(nums.begin(), nums.end());    
}

{% endhighlight %}

1. 从后往前先求出nums[i] > nums[i-1] 的index1
2. 从后往前找到第一个逼nums[index1-1]大的数, index2
3. swap(nums[index1-1], nums[index2])
4. reverse(nums.begin()+index1, nums.end());

{% highlight cpp %}

void nextPermutation(vector<int>& nums) {
  int idx1 = nums.size() - 1;
  while (idx1 > 0 && nums[idx1-1] >= nums[idx1]) idx1--;
  if (idx1 == 0) {
    reverse(nums.begin(), nums.end());
    return;
  }

  int idx2 = nums.size() - 1;
  while (nums[idx1-1] >= nums[idx2]) idx2--;
  swap(nums[idx1-1], nums[idx2]);
  reverse(nums.begin()+idx1, nums.end());
}

{% endhighlight %}
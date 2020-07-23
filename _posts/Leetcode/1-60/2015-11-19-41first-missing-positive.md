---
layout: post
title: "41.First Missing Positive"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

bucket sort

{% highlight cpp %}

int firstMissingPositive(vector<int>& nums) {
  bucket(nums);
  for (int i = 0; i < nums.size(); i++) {
    if (i+1 != nums[i]) return i+1;
  }

  return nums.size()+1;
}

void bucket(vector <int>& nums) {
  for (int i = 0; i < nums.size(); i++) {
    while (nums[i] != i+1 && nums[i] <= nums.size() 
          && nums[i] > 0 && nums[i] != nums[nums[i]-1]) {
      swap(nums[i], nums[nums[i]-1]);
    }
  }
}

{% endhighlight %}
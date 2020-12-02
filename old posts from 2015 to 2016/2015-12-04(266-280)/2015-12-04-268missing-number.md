---
layout: post
title: "268.Missing Number"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

bucket sort

{% highlight cpp %}

int missingNumber(vector<int>& nums) {
  sort(nums);

  for (int i = 0; i < nums.size(); i++) {
    if (nums[i] != i)
      return i;
  }

  return nums.size();
}

void sort(vector <int>& nums) {
  for (int i = 0; i < nums.size(); i++) {
    while (nums[i] >= 0 && nums[i] < nums.size() && nums[i] != i && nums[i] != nums[nums[i]]) {
      swap(nums[i], nums[nums[i]]);
    }
  }
}

{% endhighlight %}

the numbers of all n distinct numbers are n*(n+1)/2,
then substract everything from that

{% highlight cpp %}

int missingNumber(vector<int>& nums) {
  int n = nums.size();
  int ans = n*(n+1)/2;
  for (int i = 0; i < nums.size(); i++)
    ans -= nums[i];
  return ans;    
}

{% endhighlight %}

---
layout: post
title: "128. Longest Consecutive Sequence"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

for each number, extend it to left and right and update results

{% highlight cpp %}

class Solution {
public:
  int longestConsecutive(vector<int>& nums) {
    set <int> s;
    for (auto num : nums) s.insert(num);
    int ans = 0;

    for (int i = 0; i < nums.size(); i++) {
      int left = 0, right = 0;
      for (int j = nums[i]; s.count(j); j++) {
        left++;
        s.erase(j);
      }

      for (int j = nums[i]-1; s.count(j); j--) {
        right++;
        s.erase(j);
      }

      ans = max(ans, left+right);
    }

    return ans;
  }
};



{% endhighlight %}
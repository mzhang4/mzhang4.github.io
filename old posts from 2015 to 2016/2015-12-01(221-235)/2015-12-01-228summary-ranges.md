---
layout: post
title: "228.Summary Ranges"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

一个range一个range的进行合并

{% highlight cpp %}

vector<string> summaryRanges(vector<int>& nums) {
  vector <string> ans;
  for (int i = 0; i < nums.size(); i++) {
    int start = nums[i];
    while (i+1 < nums.size() && nums[i]+1 == nums[i+1]) i++;
    string cur = to_string(start);
    if (start != nums[i]) cur += "->" + to_string(nums[i]);
    ans.push_back(cur);
  }
  return ans;
}

{% endhighlight %}
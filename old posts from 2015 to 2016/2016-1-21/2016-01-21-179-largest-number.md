---
layout: post
title: "179. Largest Number"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

write my own cmp, let the number which producers the largest number go first

{% highlight cpp %}

bool cmp(int a, int b) {
  string aa = to_string(a);
  string bb = to_string(b);
  return aa + bb > bb + aa;
}

class Solution {
public:
  string largestNumber(vector<int>& nums) {
    sort(nums.begin(), nums.end(), cmp);
    string ans;
    for (auto num : nums) ans += to_string(num);
    while (ans[0] == '0' && ans.length() > 1) ans = ans.substr(1);
    return ans;
  }
};

{% endhighlight %}
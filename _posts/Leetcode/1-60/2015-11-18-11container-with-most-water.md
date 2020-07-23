---
layout: post
title: "11.Container With Most Water"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

夹逼法
// 正确性的验证，欠费

{% highlight cpp %}

int maxArea(vector<int>& height) {
  auto a = height.begin(), b = prev(height.end());
  int ans = 0;
  
  while (b > a) {
    ans = max(ans, (int)((b-a) * min(*b,*a)));
    if (*b>*a) a++;
    else b--;
  }

  return ans;
}

{% endhighlight cpp %}
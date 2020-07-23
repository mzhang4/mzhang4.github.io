---
layout: post
title: "217.Contains Duplicate"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

set

{% highlight cpp %}

bool containsDuplicate(vector<int>& nums) {
  set <int> dic;
  for (auto n : nums) {
    if (dic.count(n)) return true;
    dic.insert(n);
  }    
  return false;
}

{% endhighlight %}
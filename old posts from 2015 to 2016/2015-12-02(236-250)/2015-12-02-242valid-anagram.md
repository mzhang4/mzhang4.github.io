---
layout: post
title: "242.Valid Anagram"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

{% highlight cpp %}

bool isAnagram(string s, string t) {
  sort(s.begin(), s.end());
  sort(t.begin(), t.end());
  return s == t;    
}

{% endhighlight %}

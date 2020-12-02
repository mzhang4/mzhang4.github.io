---
layout: post
title: "28.Implement strStr()"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

brute force

{% highlight cpp %}

int strStr(string haystack, string needle) {
  if (needle == "") return 0;
  
  int p = 0, q = 0;
  while (p < haystack.length()) {
    if (haystack[p] == needle[q]) {
      p++; q++;
      if (q == needle.length())
        return p - q;
    }
    else {
      p = p - q + 1;
      q = 0;
    }
  }
  return -1;
}

{% endhighlight %}

kmp

{% highlight cpp %}
// 欠费中
{% endhighlight %}
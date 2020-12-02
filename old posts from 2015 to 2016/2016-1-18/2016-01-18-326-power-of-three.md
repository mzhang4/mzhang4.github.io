---
layout: post
title: "326. Power of Three"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

{% highlight cpp %}

class Solution {
public:
  bool isPowerOfThree(int n) {
      return n > 0 && (n == 1 || (n%3==0&&isPowerOfThree(n/3)));
  }
};

{% endhighlight %}

用log来计算

{% highlight cpp %}

class Solution {
public:
  bool isPowerOfThree(int n) {
    if (n <= 0) return false;
    int k = log10(n)/log10(3);
    return pow(3, k) == n;
  }
};

{% endhighlight %}
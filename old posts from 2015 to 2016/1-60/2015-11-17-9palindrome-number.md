---
layout: post
title: "9.Palindrome Number"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

求出x的最高位，每次对最高位和最低位进行比较
或者直接求出to_string(x)进行比较

{% highlight cpp %}

bool isPalindrome(int x) {
  if (x < 0) return false;
    
  int d = 1;
  while (x/d>=10) d *=10;
  while (x>0) {
    if (x/d != x%10) return false;
    x %= d;
    x /= 10;
    d /= 100;
  }

  return true;
}

{% endhighlight %}
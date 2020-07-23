---
layout: post
title: "7.Reverse Integer"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

最从低位开始对x进行处理， ans ＝ ans＊10＋x％10， 注意越界的处理

{% highlight cpp %}

int reverse(int x) {
  if (x == INT_MIN) return 0;
  int sign = x > 0 ? 1: -1;
  x = abs(x);
  int ans = 0;
  
  while (x) {
    if (ans > INT_MAX/10 || (ans == INT_MAX/10 && x%10>INT_MAX%10))
        return 0;
    ans *= 10;
    ans += x%10;
    x /= 10;
  }
  
  return ans * sign;
}

{% endhighlight %}
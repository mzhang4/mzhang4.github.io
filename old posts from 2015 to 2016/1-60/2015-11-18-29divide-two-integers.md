---
layout: post
title: "29.Divide two integers"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

1. 算出divisor向右移动多少位不大于dividend
2. dividend － divisor
3. ans ＋＝ 1 << step
4. 如果dividend 大于 divisor， 则divisor 向左移，重复第一步

{% highlight cpp %}

typedef long long LL;

int divide(int dividend, int divisor) {
  LL dnd = dividend;
  LL div = divisor;
  
  int sign = (dnd < 0) ^ (div < 0);
    
  dnd = abs(dnd);
  div = abs(div);
  LL divn = div;
  LL ansn = 1;

  while (dnd >= (divn << 1)) {
    divn <<= 1;
    ansn <<= 1;
  }

  LL ans = 0;
  while (divn >= div) {
    if (dnd >= divn) {
      ans += ansn;
      dnd -= divn;
    }
    ansn >>= 1;
      divn >>= 1;
  }

  if (sign == 0) return ans > INT_MAX ? INT_MAX : ans;
  return ans - 1> INT_MAX ? INT_MAX : ~ans + 1;
}

{% endhighlight %}

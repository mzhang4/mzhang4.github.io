---
layout: post
title: "201. Bitwise AND of Numbers Range"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

只要有一位出现0， 则该位永远为0，所以只要求出m和n从最高位开始那些相同的位数即可。
如果某一位不相同，则m^n就可以得到0，
如果某位相同，但是这一位的高位还有不同的位数，则m－n之间必然存在一个数使得该位置0

{% highlight cpp %}

class Solution {
public:
  int rangeBitwiseAnd(int m, int n) {
    int p = 0;
    
    while (m != n) {
      n >>= 1;
      m >>= 1;
      p++;
    }

    return m << p;
  }
};

{% endhighlight %}
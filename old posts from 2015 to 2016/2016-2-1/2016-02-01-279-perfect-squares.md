---
layout: post
title: "279. Perfect Squares"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

DP. use f[i] to update f[i+k^2] = min(f[i+k^2], f[i]+1);

{% highlight cpp %}

class Solution {
public:
  int numSquares(int n) {
    vector <int> f(n+1, 0);
    for (int i = 0; i <= n; i++) f[i] = i;
    
    for (int i = 0; i < n; i++) {
      int t = 0;
      while (n - t*t >= i) {
        f[i+t*t] = min(f[i+t*t], f[i]+1);
        t++;
      }
    }

    return f[n];      
  }
};

{% endhighlight %}

***

Another solution. Lagrange's four-square theorem...
https://en.wikipedia.org/wiki/Lagrange%27s_four-square_theorem
First, while (n%4==0) n/4; Then if (n%8==7) then return 4;
At last, the number would be very small and we could try to set a*a+b*b == n, if it's possible
then return !!a+!!b, else return 3

{% highlight cpp %}

class Solution {
public:
  int numSquares(int n) {
    while (n%4 == 0) n /= 4;
    if (n%8 == 7) return 4;
    for (int a = 0; a * a <= n; a++) {
      int b = sqrt(n - a * a);
      if (a*a + b*b == n) {
        return !!a+!!b;
      }
    }
    return 3;
  }
};

{% endhighlight %}
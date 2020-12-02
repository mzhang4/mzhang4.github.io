---
layout: post
title: "168.Excel Sheet Column Title"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

10 base to 26 base, 此26进制数是从1-26 不是0-26

{% highlight cpp %}

string convertToTitle(int n) {
  string ans;
  while (n) {
    n--;
    ans += n%26+'A';
    n /= 26;
  }    
  reverse(ans.begin(), ans.end());
  return ans;
}

{% endhighlight %}
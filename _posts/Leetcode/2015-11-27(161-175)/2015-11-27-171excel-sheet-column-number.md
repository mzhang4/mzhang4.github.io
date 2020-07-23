---
layout: post
title: "171.Excel Sheet Column Number"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

n base to 10 base number

{% highlight cpp %}

int titleToNumber(string s) {
  int ans = 0;

  for (int i = 0; i < s.length(); i++) {
    ans *= 26;
    ans += s[i]-'A'+1;
  }    
  
  return ans;
}


{% endhighlight %}
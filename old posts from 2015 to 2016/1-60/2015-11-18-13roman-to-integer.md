---
layout: post
title: "13.Roman to Integer"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

对于str进行遍历，如果遇到当前字母对应的数字大于前一个字母对应的数字时，则此数为生成的新书，
结果为 curVal - 2*preVal

{% highlight cpp %}

int romanToInt(string s) {
  int ans = 0;
  int prev = INT_MAX, cur;

  for (int i = 0; i < s.length(); i++) {
    cur = getVal(s[i]);
    if (cur > prev) ans += cur - 2 * prev;
    else ans += cur;
    prev = cur;
  }

  return ans;
}

int getVal(char c) {
  switch(c) {
    case 'I': return 1;
    case 'V': return 5;
    case 'X': return 10;
    case 'L': return 50;
    case 'C': return 100;
    case 'D': return 500;
    case 'M': return 1000;
    default: return 0;
  }
}

{% endhighlight %}
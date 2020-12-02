---
layout: post
title: "44.Wildcard Matching"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

对每一个字符进行两两匹配，如果相同或者p[n]=='?', m++,n++
如果p[n]等于＊，纪录当前*位置以及m位置，n++
如果不等于＊，但是存在上一个＊的位置，则进行回述，回述到上一次＊+1的位置，m为上一次*时m的位置+1,更新上一次m的位置
否则返回false

{% highlight cpp %}

bool isMatch(string s, string p) {
  int m = 0, n = 0;
  int start = 0, ss = 0;

  while (m < s.length()) {
    if (n < p.length() && (s[m] == p[n] || p[n] == '?')) { m++; n++; continue; }
    else if (n < p.length() && p[n] == '*') { start = ++n; ss = m; continue; }
    else if (start) { n=start; m=++ss; continue; }
    return false;
  }

  while (n < p.length() && p[n] == '*') n++;
  return n == p.length();
}

{% endhighlight %}
---
layout: post
title: "58.Length of Last Word"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

细节实现题，找到最后一个非空格的ind，向前迭代，直到遇到空格结束

{% highlight cpp %}

int lengthOfLastWord(string s) {
  int last = (int)s.size() - 1;
  while (last >= 0 && isspace(s[last])) last--;
  int len = 0;
  for (; last >= 0; last--) {
    if (isspace(s[last])) break;
    len++;
  }
  return len;
}

{% endhighlight %}
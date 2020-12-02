---
layout: post
title: "65.Valid Number"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

考查对库函数strtod的使用

{% highlight cpp %}

bool isNumber(string s) {
  char* endptr;
  strtod(s.c_str(), &endptr);
  
  if (endptr == s.c_str()) return false;

  while (*endptr && isspace(*endptr)) ++endptr;
  return !*endptr;    
}

{% endhighlight %}
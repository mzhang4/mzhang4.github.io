---
layout: post
title: "20.Valid Parentheses"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

标准的stack解决的题，遇到做括号丢进stack，遇到有括号，查看是否与stack.top()相匹配，不匹配则返回false，
匹配，则将top pop出来

{% highlight cpp %}

bool isValid(string str) {
  stack <char> s;
  for (int i = 0; i < str.length(); i++) {
    if (str[i] == '(' || str[i] == '[' || str[i] == '{')
      s.push(str[i]);
    else if (!s.empty() && ok(s.top(), str[i]))
      s.pop();
    else
      return false;
  }   

  return s.empty();
}

bool ok(char s1, char s2) {
  if ((s1=='('&&s2==')') || (s1=='['&&s2==']') || (s1=='{'&&s2=='}'))
    return true;
  return false;
}

{% endhighlight %}
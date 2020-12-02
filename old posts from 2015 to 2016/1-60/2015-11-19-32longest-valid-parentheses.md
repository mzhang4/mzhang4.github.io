---
layout: post
title: "32.Longest Valid Parentheses"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

考察stack的用法，用stack记录每一个做括号，或者不合法的index,
当str为')'并且stack.top为'('，可以pop出做括号，并且更新结果

{% highlight cpp %}
int longestValidParentheses(string str) {
  stack <int> s;
  int ans = 0;
  for (int i = 0; i < str.length(); i++) {
    if (!s.empty() && str[i] == ')' && str[s.top()] == '(') {
      s.pop();
      ans = max(ans, i - (s.empty() ? -1 : s.top()));
    }
    else {
      s.push(i);
    }
  }
  return ans;
}
{% endhighlight %}

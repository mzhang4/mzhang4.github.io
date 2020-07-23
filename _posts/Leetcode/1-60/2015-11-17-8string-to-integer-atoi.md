---
layout: post
title: "8.String to Integer (atoi)"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

和上一条类似， 注意str开始可能有符号位，或有前置的空格

{% highlight cpp %}
int myAtoi(string str) {
  int ind = 0;
  int ans = 0;
  int sign = 1;

  while (isspace(str[ind])) ind++;
  if (str[ind]=='+') ind++;
  else if (str[ind]=='-') ind++, sign = -1;

  for (; ind < str.length(); ind++) {
    if (!isdigit(str[ind])) break;
    if (ans > INT_MAX/10 || (ans == INT_MAX/10 && str[ind]-'0'>INT_MAX%10))
      return sign > 0 ? INT_MAX : INT_MIN;
    ans *= 10;
    ans += (str[ind] - '0');
  }

  return ans * sign;
}

{% endhighlight %}

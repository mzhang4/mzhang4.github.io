---
layout: post
title: "125.Valid Palindrome"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

细节题

{% highlight cpp %}

bool isPalindrome(string s) {
  string ss;
  for (auto ch : s) {
    if (isalpha(ch))
      ss += tolower(ch);
    else if (isdigit(ch))
        ss += ch;
  }

  return ok(ss);
}

bool ok(string s) {
  int len = s.length();
  for (int i = 0; i < len/2; i++) {
    if (s[i] != s[len-1-i])
      return false;
  }
  return true;
}

{% endhighlight %}
---
layout: post
title: "5.Longest Palindromic Substring"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

动态规划或记忆话搜索均可，用f[i][j]表示s中从i到j是否为为回文串
f[i][j] = true if (j - i < 2 || f[i+1][j-1]) && s[i]==s[j]
Time: O(n^2), Space: O(n^2)

{% highlight cpp %}
string longestPalindrome(string s) {
  int n = s.length();
  if (!n) return s;

  bool f[n][n];
  memset(f, false, sizeof(f));
  string ans;

  for (int i = n - 1; i >= 0; i--) {
    for (int j = i; j < n; j++) {
      if ((j - i < 2 || f[i+1][j-1]) && s[i] == s[j])
        f[i][j] = true;
      if (f[i][j] && (int)ans.length() < j - i + 1) 
        ans = s.substr(i, j - i + 1);
    }
  }

  return ans;
}
{% endhighlight %}

Manacher’s algorithm
{% highlight cpp %}
// 欠费中
{% endhighlight %}



---
layout: post
title: "97. Interleaving String"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

dynamic programming

{% highlight cpp %}

class Solution {
  vector <vector <int> > f;
  string s1, s2, s3;
public:
  bool isInterleave(string s1, string s2, string s3) {
    int m = s1.length(), n = s2.length();
    if (m+n != s3.length()) return false;
    
    this->s1 = s1; this->s2 = s2; this->s3 = s3;
    
    f.resize(m+1, vector <int>(n+1, -1));
    f[0][0] = 1;
    return go(m, n);
  }
  
  int go(int m, int n) {
    int& ans = f[m][n];
    if (ans != -1) return ans;
    ans = 0;
    if (m && s1[m-1] == s3[m+n-1]) ans = go(m-1, n);
    if (n && s2[n-1] == s3[m+n-1] && !ans) ans |= go(m, n-1);
    return ans;
  }
};

{% endhighlight %}
---
layout: post
title: "132. Palindrome Partitioning II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

dp

{% highlight cpp %}

class Solution {
  vector <int> f;
  vector <vector <int> > p;
  string s;
public:
  int minCut(string s) {
    this->s = s;
    int n = s.length();
    f.resize(n+1, -1);
    
    p.resize(n, vector <int>(n, -1));
    for (int i = 0; i < n; i++) {
      for (int j = i+1; j < n; j++) {
        ok(i, j);
      }
    }

    f[n] = 0;
    
    return go(0)-1;
  }

  int go(int n) {
    int& ans = f[n];
    if (ans != -1) return ans;
    string tmp;
    ans = s.length()-n;
    for (int i = n; i < s.length(); i++) {
      tmp += s[i];
      if (p[n][i]) ans = min(ans, go(i+1)+1);
    }
    return ans;
  }

  int ok(int x, int y) {
    int& ans = p[x][y];
    if (ans != -1) return ans;
    if (x >= y) ans = 1;
    else {
      ans = s[x] == s[y] && ok(x+1, y-1);
    }
    return ans;
  }
};

{% endhighlight %}

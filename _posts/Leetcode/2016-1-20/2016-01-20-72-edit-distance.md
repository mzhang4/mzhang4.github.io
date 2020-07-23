---
layout: post
title: "72. Edit Distance"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

dynamic programming
if (w1[i] == w2[j]) f(i, j) = f(i-1, j-1);
else f(i, j) = min(f(i-1, j)+1, f(i, j-1)+1, f(i-1,j-1)+1)
boundary: if (i == 0 || j == 0) f(i, j) = i + j; 

{% highlight cpp %}

class Solution {
  vector <vector <int> > f;
  string w1, w2;
public:
  int minDistance(string word1, string word2) {
    int m = word1.length(), n = word2.length();
    w1 = word1; w2 = word2;
    f.resize(m+1, vector <int>(n+1, -1));
    return go(m, n);
  }

  int go(int x, int y) {
    int& ans = f[x][y];
    if (ans != -1) return ans;
    if (x == 0 || y == 0) ans = x+y;
    else {
      ans = go(x-1, y-1);
      if (w1[x-1] != w2[y-1])
        ans = min(ans+1, min(go(x-1, y), go(x, y-1))+1);
    }
    return ans;
  }
};

{% endhighlight %}
---
layout: post
title: "87. Scramble String"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

f[i][j][k] = true means from s1[i] to s1[i+k-1] and s2[j] to s2[j+k-1] can be scrambled
f[i][j][k] = true if and only if (f[i][j][k1] && f[i+k1][j+k1][k-k1]) || (f[i][j+k-k1][k1] && f[i+k1][j][k-1]) exists
Base case: k == 1

{% highlight cpp %}

class Solution {
  vector <vector <vector <int> > > f;
  string s1, s2;

public:
  bool isScramble(string s1, string s2) {
    this->s1 = s1; this->s2 = s2;
    if (s1.length() != s2.length()) return false;
    int m = s1.length();
    f.resize(m+1, vector <vector <int> >(m+1, vector <int>(m+1, -1)));
    return go(0, 0, m);    
  }

  int go(int x, int y, int k) {
    int& ans = f[x][y][k];
    if (ans != -1) return ans;

    ans = 0;
    if (k == 1) ans = s1[x] == s2[y];
    else {
      for (int k1 = 1; k1 < k; k1++) {
        if ((go(x, y, k1) && go(x+k1, y+k1, k-k1)) || 
            (go(x, y+k-k1, k1) && go(x+k1, y, k-k1))) {
          ans = 1;
          break;
        }
      }
    }

    return ans;
  }
};

{% endhighlight %}

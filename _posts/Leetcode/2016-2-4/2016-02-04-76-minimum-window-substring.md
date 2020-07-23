---
layout: post
title: "76. Minimum Window Substring"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

sliding window problem. use a flag to track how many status are matched.
if all status are matched, update the result and moving the start point

{% highlight cpp %}

class Solution {
public:
  string minWindow(string s, string t) {
    int f[256][2] = {0};
    for (int i = 0; i < t.length(); i++)
      f[t[i]][0]++;
    
    string ans;
    int start = 0;
    int has = 0;
    
    for (int i = 0; i < s.length(); i++) {
      if (f[s[i]][0]) {
        f[s[i]][1]++;
        if (f[s[i]][1] == f[s[i]][0])
          has++;
      }

      while (has == t.length()) {
        if (ans=="" || i-start+1 < ans.length()) ans=s.substr(start, i-start+1);
        if (f[s[start]][0]) f[s[start]][1]--;
        if (f[s[start]][1] == f[s[start]][0]-1)
          has--;
        start++;
      }
    }
    
    return ans;
  }
};

{% endhighlight %}
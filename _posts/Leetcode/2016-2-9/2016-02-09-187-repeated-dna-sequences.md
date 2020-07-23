---
layout: post
title: "187. Repeated DNA Sequences"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

sliding window

{% highlight cpp %}

class Solution {
public:
  vector<string> findRepeatedDnaSequences(string s) {
    string tmp;
    map <string , int> smap;

    for (int i = 0; i < s.length(); i++) {
      tmp += s[i];
      if (tmp.length() < 10) continue;
      if (tmp.length() > 10) tmp = tmp.substr(tmp.length() - 10, 10);
      smap[tmp]++;
    } 

    vector <string> ans;

    for (auto it : smap) {
      if (it->second > 1)
        ans.push_back(it->first);
    }

    return ans;
  }
};

{% endhighlight %}

use bit operation and dicts. 欠费
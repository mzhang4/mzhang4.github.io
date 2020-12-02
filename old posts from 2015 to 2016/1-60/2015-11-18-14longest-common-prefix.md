---
layout: post
title: "14.Longest Common Prefix"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

暴力搜索

{% highlight cpp %}

string longestCommonPrefix(vector<string>& strs) {
  if (strs.size() == 0) return "";
  
  string ans;
  for (int i = 0; i < strs[0].length(); i++) {
    bool f = true;
    for (int j = 1; j < strs.size(); j++) {
      if (i >= strs[j].length() || strs[0][i] != strs[j][i]) {
        f = false;
        break;
      }
    }
    
    if (f) ans += strs[0][i];
    else break;
  }
  
  return ans;
}

{% endhighlight %}
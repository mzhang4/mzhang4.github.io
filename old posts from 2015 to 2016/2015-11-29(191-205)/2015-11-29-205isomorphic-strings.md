---
layout: post
title: "205.Isomorphic Strings"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

set and hashmap

{% highlight cpp %}

bool isIsomorphic(string s, string t) {
  if (s.length() != t.length()) return false;

  map <char, char> dict;
  set <char> vis;

  for (int i = 0; i < s.length(); i++) {
    if ((dict.count(s[i]) && dict[s[i]] != t[i]) || (!dict.count(s[i]) && vis.count(t[i])))
      return false;
    dict[s[i]] = t[i];
    vis.insert(t[i]);
  }

  return true;
}

{% endhighlight %}
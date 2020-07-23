---
layout: post
title: "71. Simplify Path"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

stack problem

{% highlight cpp %}

class Solution {
public:
  string simplifyPath(string path) {
    path += '/';
    string ret;
    stack <string> s;
    string cur;

    for (int i = 0; i < path.length(); i++) {
      if (path[i] == '/') {
        if (cur != "") {
          if (cur==".") ;
          else if (cur==".." && !s.empty()) s.pop();
          else if (cur != "..") s.push(cur);
          cur = "";
        }
      } else {
        cur += path[i];
      }
    }

    while (!s.empty()) {
      ret = "/" + s.top() + ret;
      s.pop();
    }

    if (ret == "") ret = "/";
    return ret;
  }
};


{% endhighlight %}
---
layout: post
title: "93.Restore IP Addresses"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

标准的搜索类题bfs或者dfs题

{% highlight cpp %}

vector<string> restoreIpAddresses(string s) {
  if (s == "") return vector <string>();
  vector <string> ans;
  dfs(ans, "", 0, 0, s);
  return ans;
}

void dfs(vector <string>& ans, string cur, int step, int component, string& s) {
  if (step == s.length()) {
    if (component == 4) {
      cur = cur.substr(0, cur.length() - 1);
      ans.push_back(cur);
    }
    return;
  }

  if (s.length() - step < 4 - component || s.length() - step > 3 * (4-component))
    return;
  
  int num = 0;
  for (int i = step; i < s.length(); i++) {
    num *= 10;
    num += s[i] - '0';

    if ((s[step] == '0' && i != step) || num > 255) break;
    dfs(ans, cur + to_string(num) + ".", i + 1, component + 1, s);
  }
}

{% endhighlight %}
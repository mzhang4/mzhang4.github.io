---
layout: post
title: "17.Letter Combinations of a Phone Number"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

标准的搜索类题目， BFS, DFS均可

{% highlight cpp %}

string D[] = {"abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};
vector<string> letterCombinations(string digits) {
  vector <string> ans;
  dfs(ans, "", digits);
  return ans;
}

void dfs(vector <string>& ans, string cur, string& digits) {
  if (cur.length() == digits.length()) {
    ans.push_back(cur);
    return;
  }

  int ind = digits[cur.length()] - '2';
  string s = D[ind];
  for (int i = 0; i < s.length(); i++) {
    dfs(ans, cur + s[i], digits);
  }
}

{% endhighlight %}

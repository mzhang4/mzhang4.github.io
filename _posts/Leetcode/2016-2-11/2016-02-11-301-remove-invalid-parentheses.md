---
layout: post
title: "301. Remove Invalid Parentheses"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

dfs

{% highlight cpp %}

class Solution {
public:
  vector<string> removeInvalidParentheses(string s) {
    vector <string> ans;
    dfs(ans, 0, 0, 0, "", s);
    sort(ans.begin(), ans.end());
    ans.erase(unique(ans.begin(), ans.end()), ans.end());
    return ans;
  }
  
  void dfs(vector <string>& ans, int left, int right, int start, string cur, string s) {
    if (left == right) {
      if (ans.empty() || ans[0].length() < cur.length()) {
        ans.clear();
        ans.push_back(cur);
      } else if (!ans.empty() && ans[0].length() == cur.length()) {
        ans.push_back(cur);
      }
    }

    if (right > left || start == s.length())
      return;

    if (!isalpha(s[start]))
      dfs(ans, left, right, start+1, cur, s);

    if (s[start] == '(') {
      dfs(ans, left+1, right, start+1, cur + s[start], s);
    } else if (s[start] == ')') {
      dfs(ans, left, right+1, start+1, cur + s[start], s);
    } else {
      dfs(ans, left, right, start+1, cur + s[start], s);
    }
  }
};

{% endhighlight %}

{% highlight cpp %}

class Solution {
public:
  vector<string> removeInvalidParentheses(string s) {
    vector <string> ans;
    queue <string> q;
    set <string> vis;
    bool f = false;

    q.push(s);

    while (!q.empty()) {
      string tmp = q.top(); q.pop();
      
      if (vis.count(tmp)) continue;
      vis.insert(tmp);

      int d = calc(tmp);
      if (d == 0) {
        ans.push_back(tmp);
        f = true;
      }

      if (f) continue;

      for (int i = 0; i < tmp.length(); i++) {
        if (tmp[i] == '(' || tmp[i] == ')') {
          string next = tmp.substr(0, i) + tmp.substr(i+1);
          if (!vis.count(next) && calc(vis) < d) {
            q.push(next);
          }
        }
      }
    }

    return ans;  
  }
};

{% endhighlight %}
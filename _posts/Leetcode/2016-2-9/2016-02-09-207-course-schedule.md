---
layout: post
title: "207. Course Schedule"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

topsort

{% highlight cpp %}

typedef pair <int, int> PII;

class Solution {
  vector <int> c;
  vector <int> ret;
  map <int, vector <int> > G;
  int t;
  int n;

public:
  vector <int> findOrder(int numCourses, vector<pair<int, int>>& prerequisites) {
    c.resize(numCourses, 0);
    ret.resize(numCourses, 0);
    G.clear();
    t = numCourses;
    n = numCourses;

    for (int i = 0; i < prerequisites.size(); i++) {
      PII p = prerequisites[i];
      G[p.second].push_back(p.first);
    }

    for (int i = 0; i < numCourses; i++) {
      if (!c[i]) {
        if (!dfs(i))  return vector <int>();
      }
    }

    return ret;
  }

  bool dfs(int u) {
    c[u] = -1;
    
    vector <int> vs = G[u];
    for (auto v : vs) {
        if (c[v] == -1) return false;
        if (!c[v] && !dfs(v)) return false;
    }

    c[u] = 1;
    ret[--t] = u;
    return true;
  }
};

{% endhighlight %}
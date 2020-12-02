---
layout: post
title: "126. Word Ladder II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

BFS求最短路径，并且维护一个father表，最后求解即可

{% highlight cpp %}

typedef pair <string, int> PSI;

class Solution {
public:
    vector<vector<string> > findLadders(string beginWord, string endWord, unordered_set<string> &wordList) {
    int n = wordList.size();
    
    unordered_set <string> vis;
    queue <PSI> q;
    map <string, vector <string> > father;
    
    q.push(PSI(beginWord, 1));
    int step = -1;
    
    while (!q.empty()) {
      string s = q.front().first;
      int curStep = q.front().second;
      q.pop();
      
      if (step != -1 && s != endWord) continue;
      if (vis.count(s)) continue;
      if (s == endWord) step = curStep;
      
      vis.insert(s);
      
      for (int i = 0; i < s.length(); i++) {
        string tmp = s;
        for (char ch = 'a'; ch <= 'z'; ch++) {
          tmp[i] = ch;
          if (wordList.count(tmp) && !vis.count(tmp)) {
            q.push(PSI(tmp, curStep+1));
            father[tmp].push_back(s);
          }
        }
      }
    }

    vector <vector <string> > ans;

    buildResult(ans, beginWord, endWord, vector <string>(), father, step - 1);
        
    return ans;
  }
    
  void buildResult(vector <vector<string> >& ans, string beginWord, string endWord, vector <string> cur,
    map <string, vector <string> >& father, int step) {
    cur.insert(cur.begin(), endWord);
    if (beginWord == endWord) {
      ans.push_back(cur);
      return;
    }          
        
    if (step == 0)
      return;
    
    vector <string> fatherStr = father[endWord];
        
    for (int i = 0; i < fatherStr.size(); i++) {
      buildResult(ans, beginWord, fatherStr[i], cur, father, step-1);
    }
  }
};

{% endhighlight %}
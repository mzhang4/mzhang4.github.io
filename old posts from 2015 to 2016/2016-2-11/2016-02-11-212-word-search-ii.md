---
layout: post
title: "212. Word Search II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

Trie+dfs

{% highlight cpp %}

typedef pair<bool, bool> PBB;
int dx[] = {0, 0, 1, -1};
int dy[] = {1, -1, 0, 0};

class TrieNode {
public:
  bool isKey;
  TrieNode* next[26];
  TrieNode() {
    isKey = false;
    for (int i = 0; i < 26; i++) {
      next[i] = nullptr;
    }
  }
};

class Trie {
public:
  Trie() {
    root = new TrieNode();
  }

  void add(string s) {
    TrieNode* tmp = root;
    for (int i = 0; i < s.length(); i++) {
      if (!tmp->next[s[i]-'a']) tmp->next[s[i]-'a'] = new TrieNode();
      tmp = tmp->next[s[i]-'a'];
    }

    tmp->isKey = true;
  }

  PBB search(string s) {
    TrieNode* tmp = root;
    for (int i = 0; i < s.length(); i++) {
      if (!tmp->next[s[i]-'a']) return PBB(false, false);
      tmp = tmp->next[s[i]-'a'];
    }
    return PBB(true, tmp->isKey);
  }

  TrieNode* root;
};

class Solution {
  Trie* trie;
  int m, n;
public:
  vector<string> findWords(vector<vector<char>>& board, vector<string>& words) {
    if (board.empty()) return vector <string>();

    trie = new Trie();
    for (int i = 0; i < words.size(); i++) trie->add(words[i]);
    
    m = board.size();
    n = board[0].size();
    set <string> ans;
    vector <vector <bool> > vis(m, vector <bool>(n, false));
    for (int i = 0; i < m; i++) {
      for (int j = 0; j < n; j++) {
        dfs(ans, i, j, "", vis, board);
      }
    }

    return vector<string>(ans.begin(), ans.end());
  }

  void dfs(set <string>& ans, int x, int y, string cur, vector <vector <bool> >& vis, vector <vector <char> >& board) {
    cur += board[x][y];
    
    PBB pbb = trie->search(cur);
    if (!pbb.first) return;
    if (pbb.second) ans.insert(cur);

    vis[x][y] = true;
    for (int i = 0; i < 4; i++) {
      int tx = x + dx[i];
      int ty = y + dy[i];
      if (valid(tx, ty) && !vis[tx][ty]) {
        dfs(ans, tx, ty, cur, vis, board);
      }
    }

    vis[x][y] = false;
  }
  
  bool valid(int x, int y) {
    if (x < 0 || y < 0 || x >= m || y >= n)
      return false;
    return true;
  }
};

{% endhighlight %}
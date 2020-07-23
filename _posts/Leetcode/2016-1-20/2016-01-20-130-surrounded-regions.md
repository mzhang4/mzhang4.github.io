---
layout: post
title: "130. Surrounded Regions"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

for all 'O's in the edge do dfs or bfs

{% highlight cpp %}

typedef pair<int, int> PII;

typedef pair<int, int> PII;

class Solution {
  int m, n;
  vector <vector <bool>> vis;
public:
  void solve(vector<vector<char>>& board) {
    m = board.size();
    n = m == 0 ? 0 : board[0].size();
    if (!m || !n) return;
    
    vis.resize(m, vector <bool>(n, false));

    int a[] = {0, m-1};
    int b[] = {0, n-1};

    for (int i = 0; i < 2; i++) {
      for (int j = 0; j < n; j++) {
        if (board[a[i]][j] == 'O' && !vis[a[i]][j]) {
          go(a[i], j, board);
        }
      }

      for (int j = 0; j < m; j++) {
        if (board[j][b[i]] == 'O' && !vis[j][b[i]]) {
          go(j, b[i], board);
        }
      }
    }

    for (int i = 0; i < m; i++) {
      for (int j = 0; j < n; j++) {
        if (board[i][j] == 'O' && !vis[i][j]) board[i][j] = 'X';
      }
    }
  }

  void go(int x, int y, vector<vector<char>>& board) {
    queue <PII> q;
    q.push(PII(x, y));
    
    int dx[] = {0, 0, 1, -1};
    int dy[] = {1, -1, 0, 0};
    
    while (!q.empty()) {
      PII p = q.front(); q.pop();
      if (vis[p.first][p.second]) continue;
      vis[p.first][p.second] = true;
      for (int i = 0; i < 4; i++) {
        int tx = dx[i] + p.first;
        int ty = dy[i] + p.second;
        if (valid(tx, ty) && board[tx][ty] == 'O' && !vis[tx][ty])
         q.push(PII(tx, ty));
      }
    }
  }
  
  bool valid(int x , int y) {
    if (x < 0 || y < 0 || x >= m || y >= n)
      return false;
    return true;
  }
    
};

{% endhighlight %}

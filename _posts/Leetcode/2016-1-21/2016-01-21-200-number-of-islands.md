---
layout: post
title: "200. Number of Islands"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

floodfill bfs or dfs

{% highlight cpp %}

typedef pair<int, int> PII;
int dx[] = {0, 0, 1, -1};
int dy[] = {1, -1, 0, 0};

class Solution {
public:
  int numIslands(vector<vector<char>>& grid) {
    int ans = 0;
    int m = grid.size();
    int n = m == 0 ? 0 : grid[0].size();
    vector <vector <bool> > vis(m, vector <bool>(n, false));

    for (int i = 0; i < m; i++) {
      for (int j = 0; j < n; j++) {
        if (grid[i][j] == '1' && !vis[i][j]) {
          ans++;
          queue <PII> q; q.push(PII(i, j));
          while (!q.empty()) {
            PII p = q.front(); q.pop();
            if (vis[p.first][p.second]) continue;
            vis[p.first][p.second] = true;
            for (int k = 0; k < 4; k++) {
              int tx = dx[k] + p.first;
              int ty = dy[k] + p.second;
              if (tx >= 0 && ty >= 0 && tx < m && ty < n && !vis[tx][ty] && grid[tx][ty] == '1') {
                q.push(PII(tx, ty));
              }
            }
          }
        }
      }
    }

    return ans;
  }
};

{% endhighlight %}
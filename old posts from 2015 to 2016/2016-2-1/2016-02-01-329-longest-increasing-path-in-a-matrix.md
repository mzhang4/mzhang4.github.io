---
layout: post
title: "329. Longest Increasing Path in a Matrix"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

DP. f[i][j] = max(f[i][j], f[i+dx[k]][j+dy[k]]+1); (if and only if mat[i][j] > f[i+dx[k]][j+dy[k]])

{% highlight cpp %}

int dx[] = {0, 0, 1, -1};
int dy[] = {1, -1, 0, 0};

class Solution {
  vector <vector <int> > f;
  vector <vector <int> > mat;
  int m, n;
public:
  int longestIncreasingPath(vector<vector<int> >& matrix) {
    mat = matrix;
    m = mat.size();
    n = m == 0 ? 0 : mat[0].size();
    f.resize(m, vector <int>(n, -1));

    int ans = 0;
    for (int i = 0; i < m; i++) {
      for (int j = 0; j < n; j++) {
        ans = max(ans, go(i, j));
      }
    }

    return ans;
  }

  int go(int x, int y) {
    int& ans = f[x][y];
    if (ans != -1) return ans;

    ans = 1;
    for (int i = 0; i < 4; i++) {
      int tx = x + dx[i];
      int ty = y + dy[i];
      if (valid(tx, ty) && mat[x][y] > mat[tx][ty]) {
        ans = max(ans, go(tx, ty)+1);
      }
    }

    return ans;
  }

  bool valid(int x, int y) {
    if (x < 0 || y < 0 || x >= m || y >= n)
      return false;
    return true;
  }
};

{% endhighlight %}
---
layout: post
title: "36.Valid Sudoku"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

细节题，分别判断，行，列和九宫格是否合法

{% highlight cpp %}

bool isValidSudoku(vector<vector<char>>& board) {
  bool f[9];
  
  for (int i = 0; i < 9; i++) {
    // row i 0 - 9
    memset(f, false, sizeof(f));
    for (int j = 0; j < 9; j++) {
      if (!isdigit(board[i][j])) continue;
      if (f[board[i][j] - '1']) return false;
      f[board[i][j] - '1'] = true;
    }

    memset(f, false, sizeof(f));
    for (int j = 0; j < 9; j++) {
      if (!isdigit(board[j][i])) continue;
      if (f[board[j][i] - '1']) return false;
      f[board[j][i] - '1'] = true;
    }
  }

  for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 3; j++) {
      memset(f, false, sizeof(f));
      for (int row = i*3; row < i*3+3; row++) {
        for (int col = j*3; col < j*3+3; col++) {
          if (!isdigit(board[row][col])) continue;
          if (f[board[row][col] - '1']) return false;
          f[board[row][col] - '1'] = true;
        }
      }
    }
  } 
  return true;
}

{% endhighlight %}
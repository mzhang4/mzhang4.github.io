---
layout: post
title: "37.Sudoku Solver"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

dfs brute force

{% highlight cpp %}

void solveSudoku(vector<vector<char>>& board) {
	solve(board);    
}

bool solve(vector <vector<char> >& board) {
	for (int i = 0; i < 9; i++) {
		for (int j = 0; j < 9; j++) {
			if (isdigit(board[i][j])) continue;
			for (int k = 1; k <= 9; k++) {
				board[i][j] = k+'0';
				if (ok(board, i, j) && solve(board))
					return true;
			}
			board[i][j] = '.';
			return false;
		}
	}
	return true;
}

bool ok(vector <vector <char> >& board, int x, int y) {
	bool f[9];
	// row x
	memset(f, false, sizeof(f));
	for (int c = 0; c < 9; c++) {
		if (!isdigit(board[x][c])) continue;
		if(f[board[x][c]-'1']) return false;
		f[board[x][c]-'1'] = true;
	}

	// col j
	memset(f, false, sizeof(f));
	for (int r = 0; r < 9; r++) {
		if (!isdigit(board[r][y])) continue;
		if (f[board[r][y]-'1']) return false;
		f[board[r][y]-'1'] = true;
	}
	
	memset(f, false, sizeof(f));
	for (int row=x/3*3; row<x/3*3+3; row++) {
		for (int col=y/3*3; col<y/3*3+3; col++) {
			if (!isdigit(board[row][col])) continue;
			if (f[board[row][col]-'1']) return false;
			f[board[row][col]-'1'] = true;
		}
	}
	return true;
}

{% endhighlight %}
---
layout: post
title: "240. Search a 2D Matrix II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

我们发现当target小于最后一列第一行的数时，我们就可以缩小搜索的范围，去掉最后一列
或者当当前航的的最后一个数小于target的时候，我们可以将行向下移

{% highlight cpp %}

class Solution {
public:
  bool searchMatrix(vector<vector<int>>& matrix, int target) {
  	if (matrix.empty()) return false;
  	int m = matrix.size();
  	int n = matrix[0].size();

  	int r = 0, c = n - 1;
  	while (c >= 0 && r < m) {
  		if (matrix[r][c] == target) return true;
  		if (matrix[r][c] > target) c--;
  		else r++;
  	}

  	return false;
  }
};

{% endhighlight %}

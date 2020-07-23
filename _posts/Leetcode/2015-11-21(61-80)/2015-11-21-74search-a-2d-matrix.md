---
layout: post
title: "74.Search a 2D Matrix"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

不停的缩小搜索范围，类似二分法

{% highlight cpp %}

bool searchMatrix(vector<vector<int>>& matrix, int target) {
	if (matrix.size() == 0) return false;
	int r = 0, c = (int)matrix[0].size()-1;

	while (r < matrix.size() && c >= 0) {
		if (matrix[r][c] == target) return true;
		if (matrix[r][c] < target) r++;
		else c--;
	}

	return false;
}

{% endhighlight %}
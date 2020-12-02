---
layout: post
title: "223.Rectangle Area"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

细节实现题，对于n维的物体，要求它们所占有的所有空间，对于所有的[x1, x2] * [y1, y2] * [z1 * z2] .... 进行判断，
如果有一个物体在这个空间里面，则加入结果即可。

{% highlight cpp %}

int computeArea(int A, int B, int C, int D, int E, int F, int G, int H) {
	vector <int> x, y;
	x.push_back(A); x.push_back(C); x.push_back(E); x.push_back(G);
	y.push_back(B); y.push_back(D); y.push_back(F); y.push_back(H);
	sort(x.begin(), x.end());
	sort(y.begin(), y.end());
	x.erase(unique(x.begin(), x.end()), x.end());
	y.erase(unique(y.begin(), y.end()), y.end());

	int ans = 0;

	for (int i = 0; i < 3; i++) {
		for (int j = 0; j < 3; j++) {
			if (ok(x[i], x[i+1], y[j], y[j+1], A, C, B, D) || 
					ok(x[i], x[i+1], y[j], y[j+1], E, G, F, H)) {
					ans += (y[j+1]-y[j]) * (x[i+1] - x[i]);
			}
		}
	}

	return ans;
}

bool ok(int tx1, int tx2, int ty1, int ty2,
				int x1, int x2, int y1, int y2) {
	if (tx1 >= x1 && tx2 <= x2 && ty1 >= y1 && ty2 <= y2)
		return true;
	return false;
}

{% endhighlight %}
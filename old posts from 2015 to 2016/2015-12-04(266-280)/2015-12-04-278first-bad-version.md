---
layout: post
title: "278.First Bad Version"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

二分查找，找到第一个true

{% highlight cpp %}

int firstBadVersion(int n) {
  int l = 1, h = n;
  while (h > l) {
    int mid = l + (h-l)/2; 
  	if (isBadVersion(mid)) {
  		h = mid;
  	}
  	else {
  		l = mid + 1;
  	}
  }

  return l;
}

{% endhighlight %}
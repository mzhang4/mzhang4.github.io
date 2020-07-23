---
layout: post
title: "88.Merge Sorted Array"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

mergesort

{% highlight cpp %}

void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
  int k = m + n;
  while (m || n) {
    if (!m || (n && nums1[m-1]<nums2[n-1])) {
      nums1[k-1] = nums2[n-1];
      n--;
    }
    else {
      nums1[k-1] = nums1[m-1];
      m--;
    }
    k--;
  }
}

{% endhighlight %}

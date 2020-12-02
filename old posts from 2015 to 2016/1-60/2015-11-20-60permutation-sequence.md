---
layout: post
title: "60.Permutation Sequence"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

k--之后除以(n-1)!,为第i个数，一直算到k=0即可

{% highlight cpp %}

string getPermutation(int n, int k) {
  string seq(n, '1');
  string ans;
  for (int i = 0; i < n; i++) seq[i] += i;
  k--;

  int t = 1;
  for (int i = 1; i < n; i++) t*= i;

  for (; k; k %= t, t /= --n) {
    int idx = k/t;
    ans += seq[idx];
    seq.erase(seq.begin() + idx);
  }

  ans += seq;
  return ans;
}

{% endhighlight %}

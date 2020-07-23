---
layout: post
title: "264. Ugly Number II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

{% highlight cpp %}
class Solution {
public:
  int nthUglyNumber(int n) {
    priority_queue <int, vector<int>, greater<int> > pq;
    pq.push(1);
    set <int> s;
    
    for (int i = 0; i < n-1; i++) {
      int k = pq.top(); pq.pop();
      int a[] = {2, 3, 5};
      for (int j = 0; j < 3; j++) {
        if (!s.count(k*a[j]) && INT_MAX/k >= a[j]) {
          pq.push(k*a[j]);
          s.insert(k*a[j]);
        }
      }
    }
    
    return pq.top();
  }
};
{% endhighlight %}

{% highlight cpp %}

class Solution {
public:
  int nthUglyNumber(int n) {
  	vector <int> res(1, 1);
  	int it2 = 0, it3 = 0, it5 = 0;
  	while (res.size() < n) {
  		int m2 = 2*res[it2], m3 = 3*res[it3], m5 = 5*res[it5];
  		int mn = min(m2, min(m3, m5));
  		res.push_back(mn);
  		if (m2 == mn) ++it2;
  		if (m3 == mn) ++it3;
  		if (m5 == mn) ++it5;
  	}
  	return res.back();	    
  }
};

{% endhighlight %}
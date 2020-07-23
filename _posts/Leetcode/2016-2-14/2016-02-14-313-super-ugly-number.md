---
layout: post
title: "313. Super Ugly Number"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

{% highlight cpp %}

class Solution {
public:
  int nthSuperUglyNumber(int n, vector<int>& primes) {
    int N = primes.size();
    int pindex[N];
    memset(pindex, 0, sizeof(pindex));
    vector <int> ans(1, 1);
    
    while (ans.size() < n) {
      int min = 0x7FFFFFFF;
      int minp = -1;
      
      for (int i = 0; i < N; i++) {
        while ((double)ans[pindex[i]] * primes[i] <= ans.back())
          pindex[i]++;
        
        if ((double)ans[pindex[i]] * primes[i] < min) {
          min = ans[pindex[i]] * primes[i];
          minp = i;
        }
      }
        
      ans.push_back(min);
      pindex[minp]++;
    }
      
    return ans.back();
  }
};

{% endhighlight %}
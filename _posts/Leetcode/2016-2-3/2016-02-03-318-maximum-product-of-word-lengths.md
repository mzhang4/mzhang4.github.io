---
layout: post
title: "318. Maximum Product of Word Lengths"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

Bit Manipulation

{% highlight cpp %}

class Solution {
public:
  int maxProduct(vector<string>& words) {
    int n = words.size();
    vector <int> nums(n, 0);

    for (int i = 0; i < n; i++) {
      for (int j = 0; j < words[i].length(); j++) {
        nums[i] |= (1 << int(words[i][j] - 'a'));
      }
    }
    
    int ans = 0;
    for (int i = 0; i < n; i++) {
      for (int j = i+1; j < n; j++) {
        if (!(nums[i] & nums[j])) {
          ans = max(ans, int(words[i].length() * words[j].length()));
        }
      }
    }
    return ans;
  }
};

{% endhighlight %}
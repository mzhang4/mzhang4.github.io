---
layout: post
title: "85. Maximal Rectangle"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

本题和largest retangle是一样的题目

{% highlight cpp %}

class Solution {
public:
  int maximalRectangle(vector<vector<char>>& matrix) {
    int m = matrix.size();
    int n = m == 0 ? 0 : matrix[0].size();
    int ans = 0;
    
    vector <int> dp(n, 0);

    for (int i = 0; i < m; i++) {
      for (int j = 0; j < n; j++) {
        if (matrix[i][j] == '1') {
          dp[j]++;
        }
        else {
          dp[j] = 0;
        }
      }
      ans = max(ans, getLargest(dp));
    }

    return ans;
  }

  int getLargest(vector <int> vect) {
    int ans = 0;
    vect.push_back(0);
    stack <int> s;

    for (int i = 0; i < vect.size(); ) {
      if (s.empty() || vect[s.top()] < vect[i]) {
        s.push(i++);
      }
      else {
        int tmp = s.top();
        s.pop();
        ans = max(ans, vect[tmp] * (s.empty() ? i : i - s.top() - 1));
      }
    }

    return ans;
  }
};

{% endhighlight %}

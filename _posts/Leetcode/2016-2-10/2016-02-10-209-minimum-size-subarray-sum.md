---
layout: post
title: "209. Minimum Size Subarray Sum"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

背包超时，用dfs (题目审错，都不对)

{% highlight cpp %}

typedef pair <int, int> PII;

typedef pair <int, int> PII;

class Solution {
public:
  int minSubArrayLen(int s, vector<int>& nums) {
    int n = nums.size();
    set <int> vis;

    sort(nums.begin(), nums.end());
    
    priority_queue <PII, vector <PII>, greater<PII> > pq;
    pq.push(PII(0, 0));

    while (!pq.empty()) {
      int ind = pq.top().first; 
      int step = pq.top().second;
      pq.pop();

      if (vis.count(ind)) continue;
      vis.insert(ind);

      for (int j = 0; j < n; j++) {
        if (ind+nums[j] > s) continue;
        if (ind + nums[j] == s) return step+1;
        pq.push(PII(ind+nums[j], step+1));
      }
    }

    return 0;
  }
};

{% endhighlight %}

dfs

{% highlight cpp %}

class Solution {
public:
  int minSubArrayLen(int s, vector<int>& nums) {
    int ans = 0;
    sort(nums.begin(), nums.end());
    dfs(ans, 0, 0, s, nums.size());
    return ans;    
  }

  void dfs(int& ans, int step, int start, int s, vector <int> nums) {
    if (s == 0) {
      ans = min(ans, step);
      return;
    }

    if (start >= nums.size()) return;

    dfs(ans, step+1, start+1, s-nums[start], nums);
    dfs(ans, step, start+1, s, nums);
  }
};

{% endhighlight %}

应该用sliding window

{% highlight cpp %}

class Solution {
public:
  int minSubArrayLen(int s, vector<int>& nums) {
    int ans = 0;
    int start = 0;
    int sum = 0;
    
    for (int i = 0; i < nums.size(); i++) {
      sum += nums[i];
      while (sum >= s) {
          if (!ans || ans > i-start+1) ans = i-start+1;
          sum -= nums[start++]; 
      }
    }
    
    return ans;
  }
};

{% endhighlight %}
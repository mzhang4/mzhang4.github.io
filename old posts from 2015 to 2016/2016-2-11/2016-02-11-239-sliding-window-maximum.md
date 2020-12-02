---
layout: post
title: "239. Sliding Window Maximum"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

{% highlight cpp %}

class Solution {
public:
  vector<int> maxSlidingWindow(vector<int>& nums, int k) {
    vector <int> ans;
    priority_queue <int> pq;
    multiset <int> s;

    for (int i = 0; i < nums.size(); i++) {
      s.insert(nums[i]);
      pq.push(nums[i]);
      if (s.size() < k) continue;
      if (s.size() > k) s.erase(s.find(nums[i-k]));
      while (s.find(pq.top()) == s.end()) pq.pop();
      ans.push_back(pq.top());
    }         

    return ans;
  }
};

{% endhighlight %}

It would be much faster if I use deque

{% highlight cpp %}

class Solution {

public:
  vector<int> maxSlidingWindow(vector<int>& nums, int k) {
    deque <int> dq;
    vector <int> ans;
    for (int i = 0; i < nums.size(); i++) {
      while (!dq.empty() && nums[dq.back()] < nums[i]) {
        dq.pop_back();
      }

      dq.push_back(i);
      if (dq.front() == i-k) dq.pop_front();
      if (i >= k - 1) ans.push_back(nums[dq.front()]);
    }
    
    return ans;
  }
};

{% endhighlight %}
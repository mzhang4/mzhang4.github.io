---
layout: post
title: "84. Largest Rectangle in Histogram"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

维护一个stack，里面保存每一个bar的长度（bar的长度应该生序排列），如果当前bar的长度小于stack顶部bar的长度，
则开始pop，我们也可以知道对于此顶部的bar，他应该可以形成的面积为height[bar]*(i-s里面倒数第二个index- 1)
ps: 很轻易的我们可以想到 i－s.top() 里面所有的数都是闭s.top()大的，否则s.top()应该由比他小的那个数pop出来，
然后我们也可以知道s.top()-(s里面倒数第二个index+1)也是闭s.top()大的，否则的话，如果由于个数比s.top()小，那么
s里面倒数第二个index就会被这个数pop出来了，这样的话 我们就可以得到对于某一个bar他最大可以形成多大的面积。

{% highlight cpp %}

class Solution {
public:
  int largestRectangleArea(vector<int>& heights) {
    stack <int> s;
    int ans = 0;
    heights.push_back(0);

    for (int i = 0; i < heights.size(); ) {
      if (!s.empty() && heights[s.top()] > heights[i]) {
        int tmp = s.top();
        s.pop();
        ans = max(ans, s.empty()? i * heights[tmp] : heights[tmp]*(i-s.top()-1));
      }
      else {
        s.push(i++);
      }
    }

    return ans;
  }
};

{% endhighlight %}

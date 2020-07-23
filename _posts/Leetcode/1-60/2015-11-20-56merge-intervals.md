---
layout: post
title: "56.Merge Intervals"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

细节实现题，先对intervals进行sort，然后一个一个进行merge，check当前的开始是不是比之前的小，如果小则merge，如果大则push


{% highlight cpp %}
bool cmp(Interval& a, Interval& b) {
  if (a.start != b.start)
    return a.start < b.start;
  return a.end < b.end; 
}

vector<Interval> merge(vector<Interval>& intervals) {
  sort(intervals.begin(), intervals.end(), cmp);
  vector <Interval> ans;
  for (int i = 0; i < intervals.size(); i++) {
    if (!i) ans.push_back(intervals[i]);
    else {
      if (intervals[i].start <= ans.back().end) {
        ans.back().end = max(ans.back().end, intervals[i].end);
      }
      else
        ans.push_back(intervals[i]);
    }
  }
  return ans;
}

{% endhighlight %}
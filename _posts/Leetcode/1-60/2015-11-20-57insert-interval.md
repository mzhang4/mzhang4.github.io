---
layout: post
title: "57.Insert Interval"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

最简单的方法就是将新的interval加入进去，排序，按照上一条的方法进行merge即可
另一种方法是对intervals进行遍历，不停的更新newInterval的上界与下届 （会超时，原因是erase操作很费时）
{% highlight cpp %}

vector<Interval> insert(vector<Interval>& intervals, Interval newInterval) {
  vector <Interval>::iterator it = intervals.begin();
  while (it != intervals.end()) {
    if (it->start > newInterval.end) {
      intervals.insert(it, newInterval);
      return intervals;
    } else if (it->end < newInterval.start) {
      ++it;
      continue;
    } else {
      // update
      newInterval.start = min(newInterval.start, it->start);
      newInterval.end = max(newInterval.end, it->end);
      it = intervals.erase(it);
    }
  }

  intervals.push_back(intervals.end(), newInterval);
  return intervals;
}

{% endhighlight %}

{% highlight cpp %}
vector<Interval> insert(vector<Interval> &intervals, Interval newInterval) {
  auto it = intervals.begin();
  for (;it != intervals.end(); ++it) {
    if (newInterval.start < it->start) {
      intervals.insert(it, newInterval);
      break;
    }
  }
   
  if (it == intervals.end()) intervals.push_back(newInterval);
  vector <Interval> ans;
  for (int i = 0; i < intervals.size(); i++) {
    if (!i) ans.push_back(intervals[i]);
    else if (ans.back().end >= intervals[i].start) {
      ans.back().end = max(ans.back().end, intervals[i].end);
    }
    else ans.push_back(intervals[i]);
  }
  return ans;
}
{% endhighlight %}

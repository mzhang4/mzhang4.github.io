---
layout: post
title: "49.Group Anagrams"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

两种方法，一个是对每个string进行排序，将排序后一样的单词存起来，
另一个是统计每一个字母出现的频率，根据频率的不同group单词。（稍快）

{% highlight cpp %}
vector<vector<string>> groupAnagrams(vector<string>& strs) {
  map <string, vector <string> > dict;
  for (auto str : strs) {
    string t = str;
    sort(t.begin(), t.end());
    dict[t].push_back(str);
  }

  vector <vector <string>> ans;
  for (auto it : dict) {
    sort(it.second.begin(), it.second.end());
    ans.push_back(it.second);
  }
  return ans;
}
{% endhighlight %}
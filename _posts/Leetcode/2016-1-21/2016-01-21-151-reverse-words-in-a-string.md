---
layout: post
title: "151. Reverse Words in a String"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

reverse the whole string first, then reverse word by word (but see the clarification, simply use this cannot work)

{% highlight cpp %}

class Solution {
public:
  void reverseWords(string &s) {
  	stringstream ss(s);
  	string t;
  	vector <string> vs;
  	while (ss >> t) vs.push_back(t);
  	s = "";
  	for (int i = 0; i < vs.size(); i++) {
  		if (i) s += " ";
  		s += vs[i];
  	}
  }
};

{% endhighlight %}

欠费中，O(1) space算法
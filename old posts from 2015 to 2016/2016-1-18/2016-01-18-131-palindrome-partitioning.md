---
layout: post
title: "131. Palindrome Partitioning"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

{% highlight cpp %}

class Solution {
	map <string, vector<vector<string> > > f;

public:
  vector<vector<string> > partition(string s) {
    f.clear();
    f[""] = vector <vector <string> >(1, vector <string>(1, ""));
  	return go(s);
  }

  vector <vector <string> > go(string s) {
  	if (f.count(s)) return f[s];
  	string tmp;
  	vector <vector <string> >& ans = f[s];
  	for (int i = 0; i < s.length(); i++) {
  		tmp += s[i];
  		if (ok(tmp)) {
  			vector <vector <string> > next = go(i==s.length()-1 ? "" :s.substr(i+1));
  			for (int j = 0; j < next.size(); j++) {
  				next[i].insert(next[i].begin(), tmp);
  				ans.push_back(next[i]);
  			}
  		}
  	}
  	return ans;
	}

	bool ok(string s) {
		int len = s.length();
		for (int i = 0; i < len/2; i++) {
			if (s[i] != s[len-1-i])
				return false;
		}
		return true;
	}
};

{% endhighlight %}
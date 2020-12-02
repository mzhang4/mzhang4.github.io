---
layout: post
title: "38.Count and Say"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

细节实现题，注意细节即可

{% highlight cpp %}
string countAndSay(int n) {
  string ans = "1";
  for (int i = 0; i < n-1; i++) {
    string tmp;
    for (int j=0; j < ans.length(); j++) {
      int len = 1;
      int ind = j;
      while (j+1 < ans.length() && ans[ind]==ans[j+1]) {
        len++;
        j++;
      }
      tmp += to_string(len) + ans[ind];
    }
    ans = tmp;
  }
  return ans;
}
{% endhighlight %}
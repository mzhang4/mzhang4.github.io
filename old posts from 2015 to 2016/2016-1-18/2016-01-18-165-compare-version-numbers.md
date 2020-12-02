---
layout: post
title: "165. Compare Version Numbers"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

recursive call, be careful about the details

{% highlight cpp %}

class Solution {
public:
  int compareVersion(string version1, string version2) {
    version1 = get0(version1);
    version2 = get0(version2);

    if (version1 == "" && version2 == "") return 0;

    int ind1 = version1.find(".");
    int ind2 = version2.find(".");
    if (ind1 == string::npos) ind1 = version1.length();
    if (ind2 == string::npos) ind2 = version2.length();
    string v1 = version1.substr(0, ind1);
    string v2 = version2.substr(0, ind2);

    return v1 == v2 ? compareVersion(ind1 == (int)version1.length() ? "" : version1.substr(ind1+1), 
           ind2 == (int)version2.length()? "" : version2.substr(ind2+1)) : comp(v1, v2) ? 1 : -1;
  }

  string get0(string version) {
    if (version == "") return version;
    int ind = 0;
    while (version[ind] == '0' && ind < version.length()) ind++;
    return version.substr(ind);
  }
  
  bool comp(string v1, string v2) {
    if (v1.length() != v2.length()) {
      return v1.length() > v2.length() ? true:false;
    }
    return v1 > v2;
  }
};

{% endhighlight %}
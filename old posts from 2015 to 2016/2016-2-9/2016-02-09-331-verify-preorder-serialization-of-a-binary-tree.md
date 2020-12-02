---
layout: post
title: "331. Verify Preorder Serialization of a Binary Tree"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

recursive

{% highlight cpp %}

class Solution {
public:
  bool isValidSerialization(string preorder) {
    if (preorder == "") return true;

    for (int i = 0; i < preorder.length(); i++) {
      if (preorder[i] == ',')
        preorder[i] = ' ';
    }        

    vector <string> nodes;
    string s;
    stringstream ss(preorder);
    
    while (ss >> s) {
      nodes.push_back(s);
    }

    int step = 0;
    return valid(step, nodes) && step == nodes.size();
  }

  bool valid(int& step, vector <string>& nodes) {
    if (step >= nodes.size()) return false;
    string ch = nodes[step++];
    if (ch == "#") return true;
    else 
      return valid(step, nodes) && valid(step, nodes);
  }
};

{% endhighlight %}
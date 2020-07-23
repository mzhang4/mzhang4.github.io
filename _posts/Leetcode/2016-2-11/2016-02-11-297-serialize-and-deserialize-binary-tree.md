---
layout: post
title: "297. Serialize and Deserialize Binary Tree"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

先序遍历

{% highlight cpp %}

class Codec {
public:
  // Encodes a tree to a single string.
  string serialize(TreeNode* root) {
    if (!root) return "null";
    string ans = to_string(root->val) + " " + serialize(root->left) + " " + serialize(root->right);
    return ans;
  }

  // Decodes your encoded data to tree.
  TreeNode* deserialize(string data) {
    vector <string> vs;
    stringstream ss(data);
    string s;
    while (ss >> s) vs.push_back(s);
    int step = 0;
    return deserialize(step, vs);
  }
  
  TreeNode* deserialize(int& step, vector <string>& vs) {
    if (vs[step++] == "null") return nullptr;
    TreeNode* ans = new TreeNode(stoi(vs[step-1]));
    ans->left = deserialize(step, vs);
    ans->right = deserialize(step, vs);
    return ans;
  }
};

{% endhighlight %}
---
layout: post
title: "144. Binary Tree Preorder Traversal"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

stack

{% highlight cpp %}

class Solution {
public:
  vector<int> preorderTraversal(TreeNode* root) {
    if (!root) return vector <int>();

    stack <TreeNode*> q;
    vector <int> ans;

    q.push(root);
    
    while (!q.empty()) {
      TreeNode* tn = q.top();
      q.pop();

      ans.push_back(tn->val);
      if (tn->right) q.push(tn->right);
      if (tn->left) q.push(tn->left);
    }

    return ans;
  }
};


{% endhighlight %}
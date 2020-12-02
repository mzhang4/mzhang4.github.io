---
layout: post
title: "230. Kth Smallest Element in a BST"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

inorder

{% highlight cpp %}

class Solution {
public:
  int kthSmallest(TreeNode* root, int k) {
    TreeNode* p = root;
    stack <TreeNode*> s;

    while (p || !s.empty()) {
      while (p) {
        s.push(p);
        p = p->left;
      }

      if (!s.empty()) {
        if (--k == 0) return s.top();
        p = s.top()->right;
        s.pop();
      }
    }

    return -1;
  }
};

{% endhighlight %}
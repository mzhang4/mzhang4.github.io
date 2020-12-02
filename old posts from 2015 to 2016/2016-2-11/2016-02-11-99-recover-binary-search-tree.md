---
layout: post
title: "99. Recover Binary Search Tree"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

inorder process with stack

{% highlight cpp %}

class Solution {
public:
  void recoverTree(TreeNode* root) {
    TreeNode *t1 = nullptr, *t2 = nullptr;    
    stack <TreeNode*> s;
    TreeNode* p = root;
    TreeNode* prev = nullptr;

    while (p || !s.empty()) {
      while (p) {
        s.push(p);
        p = p->left;
      }

      if (!s.empty()) {
        TreeNode* cur = s.top(); s.pop();
        p = cur->right;
        if (prev && prev->val > cur->val) {
          if (!t1) t1 = prev;
          t2 = cur;
        }
        prev = cur;
      }
    }

    swap(t1->val, t2->val);
  }
};

{% endhighlight %}
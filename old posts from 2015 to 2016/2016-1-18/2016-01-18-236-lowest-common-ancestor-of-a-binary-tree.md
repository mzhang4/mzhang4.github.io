---
layout: post
title: "236. Lowest Common Ancestor of a Binary Tree"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

Tree, can think up of recursive calls

{% highlight cpp %}

class Solution {
public:
  TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
    if (!root) return root;

    if (root == p || root == q) return root;
    TreeNode* l = lowestCommonAncestor(root->left, p, q);
    TreeNode* r = lowestCommonAncestor(root->right, p, q);
    if (!r && !l) return nullptr;
    else if (r && l) return root;
    else if (r) return r;
    return l;
  }
};

{% endhighlight %}

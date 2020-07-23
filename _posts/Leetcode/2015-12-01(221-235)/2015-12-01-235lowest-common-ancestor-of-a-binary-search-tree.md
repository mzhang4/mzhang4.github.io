---
layout: post
title: "235.Lowest Common Ancestor of a Binary Search Tree"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}


tree, recursive

{% highlight cpp %}

TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
    if (root == p || root == q || !root) return root;
    TreeNode* left = lowestCommonAncestor(root->left, p, q);
    TreeNode* right = lowestCommonAncestor(root->right, p, q);
    if (!left || !right)
      return left ? left : right;
    return root;
}

{% endhighlight %}
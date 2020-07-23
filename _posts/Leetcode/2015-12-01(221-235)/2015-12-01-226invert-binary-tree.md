---
layout: post
title: "226.Invert Binary Tree"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

tree, recursive

{% highlight cpp %}

TreeNode* invertTree(TreeNode* root) {
  if (!root) return root;
  TreeNode* tmp = root->left;
  root->left = invertTree(root->right);
  root->right = invertTree(tmp);
  return root;
}

{% endhighlight %}
---
layout: post
title: "114.Flatten Binary Tree to Linked List"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

树问题，很容易的想到递归

{% highlight cpp %}

void flatten(TreeNode* root) {
  flat(root);     
}

TreeNode* flat(TreeNode* root) {
  if (!root) return nullptr;
  TreeNode* left = flat(root->left);
  TreeNode* right = flat(root->right);
  TreeNode* tmp = root;
  root->left = nullptr;

  tmp->right = left;
  while (tmp->right) {
    tmp = tmp->right;
  }

  tmp->right = right;
  return root;
}

{% endhighlight %}

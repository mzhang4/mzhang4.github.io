---
layout: post
title: "110.Balanced Binary Tree"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

记忆化搜索＋递归

{% highlight cpp %}

map <TreeNode*, int> dp;

bool isBalanced(TreeNode* root) {
  dp.clear();
  return balanced(root);   
}

bool balanced(TreeNode* root) {
  if(!root) return true;
  int l = depth(root->left);
  int r = depth(root->right);
  return abs(l-r) <=1 && balanced(root->left) && balanced(root->right);   
}

int depth(TreeNode* root) {
  if (!root) return 0;
  if (dp.count(root)) return dp[root];
  return dp[root] = 1 + max(depth(root->left), depth(root->right));
}

{% endhighlight %}
---
layout: post
title: "111.Minimum Depth of Binary Tree"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

标准的tree的递归题, bfs迭代也可以解决问题

{% highlight cpp %}

int minDepth(TreeNode* root) {
  if (!root) return 0;
  if (!root->left) return 1 + minDepth(root->right);
  if (!root->right) return 1 + minDepth(root->left);
  return 1 + min(minDepth(root->left), minDepth(root->right));
}

{% endhighlight %}
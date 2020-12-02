---
layout: post
title: "104.Maximum Depth of Binary Tree"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

迭代或者递归都可以。递归的话更容易理解，代码更短。 迭代的话 bfs和dfs均可

{% highlight cpp %}

int maxDepth(TreeNode* root) {
  if (!root) return 0;
  return 1 + max(maxDepth(root->left), maxDepth(root->right));
}

{% endhighlight %}

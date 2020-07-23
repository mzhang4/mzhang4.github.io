---
layout: post
title: "222. Count Complete Tree Nodes"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

calculate the rightmost hight and leftmost hight, if there are equal, then there are 
2^n-1 nodes, otherwise it equals to left + right + 1.

{% highlight cpp %}

class Solution {
public:
  int countNodes(TreeNode* root) {
    if (!root) return 0;

    int l = height(root->left, -1);
    int r = height(root->right, 1);

    if (l == r) return (1 << (l+1)) - 1;
    return 1 + countNodes(root->left) + countNodes(root->right);
  }

  int height(TreeNode* root, int dir) {
    int ans = 0;
    while (root) {
      ans++;
      if (dir == -1) root = root->left;
      if (dir == 1) root = root->right;
    }

    return ans;
  }
};

{% endhighlight %}
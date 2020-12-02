---
layout: post
title: "98. Validate Binary Search Tree"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

tree, recursion
{% highlight cpp %}

class Solution {
public:
  bool isValidBST(TreeNode* root) {
    return isValidBST(root, LLONG_MIN, LLONG_MAX); 
  }

  bool isValidBST(TreeNode* root, LL MIN, LL MAX) {
    if (!root) return true;

    return root->val > MIN && root->val < MAX &&
    isValidBST(root->left, MIN, root->val) &&
    isValidBST(root->right, root->val, MAX);
  }
};

{% endhighlight %}

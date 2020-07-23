---
layout: post
title: "106.Construct Binary Tree from Inorder and Postorder Traversal"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

方法和上一条一样

{% highlight cpp %}
map <int, int> ioMap;

TreeNode* buildTree(vector<int>& inorder, vector<int>& postorder) {
  for (int i = 0; i < inorder.size(); i++)
    ioMap[inorder[i]] = i;
  return buildTree(inorder, 0, inorder.size() - 1, postorder, 0, postorder.size() - 1);
}

TreeNode* buildTree(vector<int>& inorder, int iol, int ior, 
            vector<int>& postorder, int pol, int por) {
  if (ior < iol) return nullptr;

  TreeNode* root = new TreeNode(postorder[por]);
  int ind = ioMap[root->val];
  root->left = buildTree(inorder, iol, ind-1, postorder, pol, ind-1-iol+pol);
  root->right = buildTree(inorder, ind+1, ior, postorder, ind-iol+pol, por-1);
}

{% endhighlight %}
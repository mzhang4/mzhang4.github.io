---
layout: post
title: "105.Construct Binary Tree from Preorder and Inorder Traversal"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

根据preorder确定root node， 然后根据inorder确定他的left和right

{% highlight cpp %}

map <int, int> poMap;
map <int, int> ioMap;

TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
  poMap.clear();
  ioMap.clear();

  for (int i = 0; i < preorder.size(); i++) {
    poMap[preorder[i]] = i;
    ioMap[inorder[i]] = i;
  }

  return buildTree(preorder, 0, preorder.size()-1, inorder, 0, inorder.size()-1);
}


TreeNode* buildTree(vector<int>& preorder, int pol, int por, 
              vector<int>& inorder, int iol, int ior) {
  if (por < pol) return nullptr;

  TreeNode* root = new TreeNode(preorder[pol]);
  int ind = ioMap[root->val];
  root->left = buildTree(preorder, pol+1, ind-iol+pol, inorder, iol, ind-1);  
  root->right = buildTree(preorder, ind-iol+pol+1, por, inorder, ind+1, ior);
}

{% endhighlight %}

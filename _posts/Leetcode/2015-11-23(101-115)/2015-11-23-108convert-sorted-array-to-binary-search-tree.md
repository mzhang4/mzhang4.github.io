---
layout: post
title: "108.Convert Sorted Array to Binary Search Tree"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

递归建树即可

{% highlight cpp %}

TreeNode* sortedArrayToBST(vector<int>& nums) {
  return sortedArrayToBST(nums, 0, nums.size()-1);    
}

TreeNode* sortedArrayToBST(vector<int>& nums, int l, int r) {
  if (r < l) return nullptr;
  int mid = l + (r-l)/2;
  TreeNode* root = new TreeNode(nums[mid]);
  root->left = sortedArrayToBST(nums, l, mid-1);
  root->right = sortedArrayToBST(nums, mid+1, r);
  return root;
}

{% endhighlight %}

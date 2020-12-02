---
layout: post
title: "109.Convert Sorted List to Binary Search Tree"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

和上一条一样，只不过将数组换成了List，比较快的方法是先遍历一边list，然后按上一条方法做即可

{% highlight cpp %}

TreeNode* sortedListToBST(ListNode* head) {
  vector <int> nums;
  while (head) {
    nums.push_back(head->val);
    head=head->next;
  }
  return sortedArrayToBST(nums, 0, nums.size() - 1);
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

还有一种方法是自底向上的，非常的巧妙 *， 需要细细体会

{% highlight cpp %}

TreeNode* sortedListToBST(ListNode* head) {
  int len = 0;
  ListNode* p = head;
  while (p) {
    len++;
    p=p->next;
  }
  return sortedListToBST(head, 0, len-1);
}

TreeNode* sortedListToBST(ListNode*& head, int l, int r) {
  if (r < l) return nullptr;

  int mid = l + (r-l)/2;
  TreeNode* left = sortedListToBST(head, l, mid-1);
  TreeNode* root = new TreeNode(head->val);
  root->left = left;
  head=head->next;
  TreeNode* right = sortedListToBST(head, mid+1, r);
  root->right = right;
  return root;
}

{% endhighlight %}



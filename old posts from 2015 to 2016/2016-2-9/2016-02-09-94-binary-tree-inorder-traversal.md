---
layout: post
title: "94. Binary Tree Inorder Traversal"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

recursive

{% highlight cpp %}

class Solution {
public:
  vector<int> inorderTraversal(TreeNode* root) {
    vector <int> ans;
    inorderTraversal(ans, root);
    return ans;
  }

  void inorderTraversal(vector <int>& ans, TreeNode* root) {
    if (!root)
      return;
    inorderTraversal(ans, root->left);
    ans.push_back(root->val);
    inorderTraversal(ans, root->right);
  }
};

{% endhighlight %}

iteratively

{% highlight cpp %}

class Solution {
public:
  vector<int> inorderTraversal(TreeNode* root) {
    vector <int> ans;

    stack <TreeNode*> s;
    TreeNode* p = root;

    while (!s.empty() || p) {
      if (p != nullptr) {
        s.push(p);
        p = p->left;
      }
      else {
        p = s.top(); s.pop();
        ans.push_back(p->val);
        p = p->right;
      }
    }

    return ans;
  }
};

{% endhighlight %}
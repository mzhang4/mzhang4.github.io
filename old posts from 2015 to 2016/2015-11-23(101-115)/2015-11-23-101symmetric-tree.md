---
layout: post
title: "101.Symmetric Tree"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

同样时tree的问题，很容易的想到递归

{% highlight cpp %}

bool isSymmetric(TreeNode* root) {
  if (!root) return true;
  return isSame(root->left, root->right);
}

bool isSame(TreeNode* t1, TreeNode* t2) {
  if (!t1 && !t2) return true;
  if (!t1 || !t2) return false;
  return t1->val == t2->val && isSame(t1->left, t2->right) && isSame(t1->right, t2->left);
}

{% endhighlight %}

迭代版和same tree的方法相同

{% highlight cpp %}

bool isSymmetric(TreeNode* root) {
  if (!root) return true;

  stack <TreeNode*> s;
  s.push(root->left);
  s.push(root->right);

  while (!s.empty()) {
    TreeNode* t1 = s.top(); s.pop();
    TreeNode* t2 = s.top(); s.pop();

    if (!t1 && !t2) continue;
    if (!t1 || !t2 || t1->val != t2->val) return false;
    s.push(t1->left);
    s.push(t2->right);
    s.push(t1->right);
    s.push(t2->left);
  }

  return true;
}

{% endhighlight %}

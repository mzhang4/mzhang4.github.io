---
layout: post
title: "145. Binary Tree Postorder Traversal My Submissions Question"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

stack 

{% highlight cpp %}

class Solution {
public:
  vector<int> postorderTraversal(TreeNode* root) {
    if (!root) return vector <int>();

    vector <int> ans;
    stack <TreeNode*> s;
    TreeNode* cur = root, *prev = nullptr;

    while (cur || !s.empty()) {
      while (cur) {
        s.push(cur);
        cur = cur->left;
      }

      if (!s.empty()) {
        if ( !s.top()->right || s.top()->right == prev) {
          ans.push_back(s.top()->val);
          prev = s.top();
          s.pop();
        } else {
          cur = s.top()->right;
        }
      }
    }

    return ans;
  }
};

{% endhighlight %}
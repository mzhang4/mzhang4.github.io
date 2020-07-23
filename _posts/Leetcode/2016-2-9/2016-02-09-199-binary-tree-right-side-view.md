---
layout: post
title: "199. Binary Tree Right Side View"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

BFS

{% highlight cpp %}

typedef pair <TreeNode*, int> PTI;

class Solution {
public:
  vector<int> rightSideView(TreeNode* root) {
    if (!root) return vector <int>();
    
    vector <int> ans;
    queue <PTI> q;
    q.push(PTI(root, 1));

    while (!q.empty()) {
      TreeNode* tmp = q.front().first;
      int level = q.front().second;
      q.pop();

      if (ans.size() < level) ans.push_back(0);
      ans[level-1] = tmp->val;

      if (tmp->left) q.push(PTI(tmp->left, level+1));
      if (tmp->right) q.push(PTI(tmp->right, level+1));
    }

    return ans;
  }
};

{% endhighlight %}
---
layout: post
title: "102.Binary Tree Level Order Traversal"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

bfs遍历整棵树即可。

{% highlight cpp %}

typedef pair<TreeNode*, int> PTI;

vector<vector<int> > levelOrder(TreeNode* root) {
  vector <vector <int> > ans;
  if (!root) return ans;

  queue <PTI> q;
  q.push(PTI(root, 1));

  while (!q.empty()) {
    PTI pti = q.front(); q.pop();
    if (ans.size() < pti.second) {
      ans.push_back(vector<int>());
    }
    ans[pti.second-1].push_back(pti.first->val);

    if (pti.first->left) q.push(PTI(pti.first->left, pti.second + 1));
    if (pti.first->right) q.push(PTI(pti.first->right, pti.second + 1));
  }
  return ans;
}

{% endhighlight %}
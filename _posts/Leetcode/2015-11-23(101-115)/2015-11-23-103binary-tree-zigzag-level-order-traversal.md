---
layout: post
title: "103.Binary Tree Zigzag Level Order Traversal"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

和上一条一样，bfs遍历即可

{% highlight cpp %}

typedef pair<TreeNode*, int> PTI;

vector<vector<int> > zigzagLevelOrder(TreeNode* root) {
  vector <vector <int> > ans;
  if (!root) return ans;

  queue <PTI> q;
  q.push(PTI(root, 1));

  while (!q.empty()) {
    PTI pti = q.front(); q.pop();
    if (ans.size() < pti.second)
      ans.push_back(vector<int>());

    if (pti.second & 0x1)
      ans[pti.second-1].push_back(pti.first->val);
    else
      ans[pti.second-1].insert(ans[pti.second-1].begin(), pti.first->val);

    if (pti.first->left) q.push(PTI(pti.first->left, pti.second+1));
    if (pti.first->right) q.push(PTI(pti.first->right, pti.second+1));
  }
  return ans;
}

{% endhighlight %}
---
layout: post
title: "107.Binary Tree Level Order Traversal II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

与level order traversal I 一样

{% highlight cpp %}

typedef pair <TreeNode*, int> PTI;

vector<vector<int>> levelOrderBottom(TreeNode* root) {
  vector <vector <int>> ans;    
  if (!root) return ans;

  queue <PTI> q;
  q.push(PTI(root, 1));
  while (!q.empty()) {
    PTI pti = q.front(); q.pop();
    if (ans.size() < pti.second) {
      ans.insert(ans.begin(), vector <int>());
    }
    ans[ans.size()-pti.second].push_back(pti.first->val);

    if (pti.first->left) q.push(PTI(pti.first->left, pti.second+1));
    if (pti.first->right) q.push(PTI(pti.first->right, pti.second+1)); 
  }

  return ans;
}

{% endhighlight %}
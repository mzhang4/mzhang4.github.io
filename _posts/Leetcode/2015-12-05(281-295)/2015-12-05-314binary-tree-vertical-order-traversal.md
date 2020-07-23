---
layout: post
title: "314.Binary Tree Vertical Order Traversal"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

dfs or bfs, dfs 有问题，顺序会不对，bfs不会出现这个问题

{% highlight cpp %}

vector<vector<int>> verticalOrder(TreeNode* root) {
  if (!root) return vector <vector <int>>();
  
  map <int, vector <int> > dict;
    queue <PTI> q;
    q.push(PTI(root, 0));
    
    while (!q.empty()) {
      PTI pti = q.front(); q.pop();
      dict[pti.second].push_back(pti.first->val);
      if (pti.first->left) q.push(PTI(pti.first->left, pti.second-1));
      if (pti.first->right) q.push(PTI(pti.first->right, pti.second+1));
    }
    
    vector <vector <int> > ans;
    
    for (auto d : dict) {
      ans.push_back(d.second);    
    }

  return ans;
}

{% endhighlight %}
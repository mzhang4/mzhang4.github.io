---
layout: post
title: "116. Populating Next Right Pointers in Each Node My Submissions Question"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

bfs, but this has space compexity O(logn)

{% highlight cpp %}

typedef pair <TreeLinkNode*, int> PTI;

class Solution {
public:
  void connect(TreeLinkNode *root) {
    if (!root) return;
    
    queue <PTI> q;
    q.push(PTI(root, 0));
    while (!q.empty()) {
      PTI pti = q.front(); q.pop();
      if (!q.empty() && q.front().second == pti.second) {
        pti.first->next = q.front().first;
      }

      if (pti.first->left) q.push(PTI(pti.first->left, pti.second+1));
      if (pti.first->right) q.push(PTI(pti.first->right, pti.second+1));
    }
  }
};

{% endhighlight %}

dfs, use stack space

{% highlight cpp %}

class Solution {
public:
  void connect(TreeLinkNode *root) {
    connect(root, nullptr);    
  }

  void connect(TreeLinkNode* left, TreeLinkNode* right) {
    if (!left)  return;
    left->next = right;
    connect(left->left, left->right);
    if (right) connect(left->right, right->left);
    else connect(left->right, nullptr);
  }
};

{% endhighlight %}
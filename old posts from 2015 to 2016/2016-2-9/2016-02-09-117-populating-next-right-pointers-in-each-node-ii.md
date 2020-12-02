---
layout: post
title: "117. Populating Next Right Pointers in Each Node II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

BFS, same as previous one, but not constant space

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

DFS

{% highlight cpp %}

class Solution {
public:
  void connect(TreeLinkNode *root) {
    if (!root) return;
    TreeLinkNode dummy(-1);
    for (TreeLinkNode* prev = &dummy; root; root = root->next) {
      if (root->left) {
        prev->next = root->left;
        prev = prev->next;
      }
      if (root->right) {
        prev->next = root->right;
        prev = prev->next;
      }
    }
    connect(dummy.next);
  }
};

{% endhighlight %}

另一种BFS

{% highlight cpp %}

class Solution {
public:
  void connect(TreeLinkNode *root) {
    while (root) {
      TreeLinkNode* next = nullptr;
      TreeLinkNode* prev = nullptr;
      for (; root; root = root->next) {
        if (!next) next = root->left ? root->left : root->right;

        if (root->left) {
          if (prev) prev->next = root->left;
          prev = root->left;
        }
        if (root->right) {
          if (prev) prev->next = root->right;
          prev = root->right;
        }
      }
      root = next;
    }
  }
};

{% endhighlight %}

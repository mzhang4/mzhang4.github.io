---
layout: post
title: "173. Binary Search Tree Iterator"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

中序遍历

{% highlight cpp %}

class BSTIterator {
public:
    BSTIterator(TreeNode *root) {
      p = root;
    }

    /** @return whether we have a next smallest number */
    bool hasNext() {
      return !s.empty() || p;
    }

    /** @return the next smallest number */
    int next() {
      int ans;
      
      while (p || !s.empty()) {
        if (p) {
          s.push(p);
          p = p->left;
        } else {
          ans = s.top()->val;
          p = s.top()->right;
          s.pop();
          break;
        }
      }

      return ans;
    }
    
    TreeNode* p;
    stack <TreeNode*> s;
};


{% endhighlight %}
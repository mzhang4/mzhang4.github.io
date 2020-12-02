---
layout: post
title: "95. Unique Binary Search Trees II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

{% highlight cpp %}

class Solution {
  vector <vector <vector <TreeNode*> > > f;
public:
  vector<TreeNode*> generateTrees(int n) {
    if (n < 1) return vector <TreeNode*>();
    f.resize(n+1, vector <vector <TreeNode*> >(n+1, vector <TreeNode*>()));
    return generateTrees(1, n);
  }

  vector <TreeNode*> generateTrees(int start, int end) {
    if (end < start) {
      return vector<TreeNode*>(1, nullptr);
    }

    vector <TreeNode*>& ans = f[start][end];
    if (ans.size() != 0) return ans;

    for (int i = start; i <= end; i++) {
      vector <TreeNode*> left = generateTrees(start, i-1);
      vector <TreeNode*> right = generateTrees(i+1, end);

      for (int j = 0; j < left.size(); j++) {
        for (int k = 0; k < right.size(); k++) {
          TreeNode* root = new TreeNode(i);
          root->left = left[j];
          root->right = right[k];
          ans.push_back(root);
        }
      }
    }

    return ans;
  }
};

{% endhighlight %}
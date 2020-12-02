---
layout: post
title: "257.Binary Tree Paths"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

dfs

{% highlight cpp %}

vector<string> binaryTreePaths(TreeNode* root) {
  vector <string> ans;
  go(ans, "", root);
  return ans;    
}

void go(vector <string>& ans, string cur, TreeNode* root) {
  if (!root) return;
  if (cur != "")
    cur += "->" + to_string(root->val);
  else
    cur += to_string(root->val);

  if (!root->left && !root->right) {
    ans.push_back(cur);
    return;
  }

  go(ans, cur, root->left);
  go(ans, cur, root->right);
}

{% endhighlight %}
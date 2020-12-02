---
layout: post
title: "124. Binary Tree Maximum Path Sum"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

tree problem, easily to think up with recursive solution

{% highlight cpp %}

class Solution {
  map <TreeNode*, int> dist;
public:
  int maxPathSum(TreeNode* root) {
    if (!root) return 0;
    int tmp = root->val;
    tmp = max(tmp, tmp+path(root->left));
    tmp = max(tmp, tmp+path(root->right));
    return max(max(tmp, maxPathSum(root->left)), maxPathSum(root->right));
  }

  int path(TreeNode* root) {
    if (!root) return 0;
    if (dist.count(root)) return dist[root];
    return dist[root] = max(root->val, root->val + max(path(root->left), path(root->right)));
  }
};

{% endhighlight %}

though using recursion descent can solve the problem, but it is very slow, 
can solve it through dfs and within dfs, track the result

{% highlight cpp %}
class Solution {
public:
  int maxPathSum(TreeNode* root) {
    int ans = INT_MIN;
    dfs(root, ans);
    return ans;
  }

  int dfs(TreeNode* root, int& ans) {
    if (!root) return 0;
    int l = dfs(root->left, ans);
    int r = dfs(root->right, ans);
    ans = max(ans, root->val+max(l, 0)+max(r, 0));
    return max(l, r) > 0 ? root->val+max(l, r) : root->val;
  }
};
{% endhighlight %}
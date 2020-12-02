---
layout: post
title: "129. Sum Root to Leaf Numbers"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

{% highlight cpp%}

class Solution {
public:
  int sumNumbers(TreeNode* root) {
  	int ans = 0;
  	dfs(ans, 0, root);
  	return ans;
  }

  void dfs(int& ans, int cur, TreeNode* root) {
  	if (!root) return;
  	cur *= 10;
  	cur += root->val;
  	if (!root->left && !root->right) {
  		ans += cur;
  		return;
  	}

  	dfs(ans, cur, root->left);
  	dfs(ans, cur, root->right);
	}
};

{% endhighlight %}
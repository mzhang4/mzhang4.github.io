---
layout: post
title: "237.Delete Node in a Linked List"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

简单的细节题

{% highlight cpp %}

void deleteNode(ListNode* node) {
  node->val = node->next->val;
  ListNode* tn = node->next;
  node->next = node->next->next;
  delete tn;
}

{% endhighlight %}
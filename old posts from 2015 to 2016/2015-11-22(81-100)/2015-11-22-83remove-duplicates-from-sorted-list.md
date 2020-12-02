---
layout: post
title: "83.Remove Duplicates from Sorted List"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

细节题

{% highlight cpp %}

ListNode* deleteDuplicates(ListNode* head) {
  if (!head) return head;
  for (ListNode *prev = head, *cur = head->next; cur; cur=cur->next) {
    if (cur->val == prev->val) {
      prev->next = cur->next;
      delete cur;
    }
    else {
      prev = cur;
    }
  }
  return head;
}

{% endhighlight %}
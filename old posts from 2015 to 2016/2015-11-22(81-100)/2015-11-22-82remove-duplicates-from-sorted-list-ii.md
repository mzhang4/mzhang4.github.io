---
layout: post
title: "82.Remove Duplicates from Sorted List II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

linkedlist 的细节实现题

{% highlight cpp %}

ListNode* deleteDuplicates(ListNode* head) {
  ListNode dummy(-1);
  dummy.next = head;
  ListNode* prev = &dummy;

  while (head) {
    bool f = true;
    ListNode* cur = head;
    while (cur->next && cur->next->val == cur->val) {
      f = false;
      ListNode* tmp = cur;
      cur = cur->next;
      delete tmp;
    }

    if (!f) { 
      ListNode* tmp = cur;
      prev->next = cur->next;
      delete tmp;
    }
    else prev->next = head, prev = prev->next;
    head = prev->next;
  }

  return dummy.next;
}


{% endhighlight %}
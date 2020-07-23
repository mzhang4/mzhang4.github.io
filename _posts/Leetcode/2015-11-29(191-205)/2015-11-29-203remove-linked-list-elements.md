---
layout: post
title: "203.Remove Linked List Elements"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

细节题

{% highlight cpp %}

ListNode* removeElements(ListNode* head, int val) {
  ListNode dummy(-1);
  dummy.next = head;
  ListNode* cur = &dummy;

  while (cur->next) {
    if (cur->next->val == val) {
      ListNode* tmp = cur->next;
      cur->next = cur->next->next;
      delete tmp;
    }
    else {
        cur = cur->next;
    }
  }
  return dummy.next;
}

{% endhighlight %}

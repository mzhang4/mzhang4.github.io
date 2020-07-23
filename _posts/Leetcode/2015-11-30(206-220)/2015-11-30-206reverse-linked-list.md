---
layout: post
title: "206.Reverse Linked List"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

头插法

{% highlight cpp %}

ListNode* reverseList(ListNode* head) {
  ListNode dummy(-1);
  while (head) {
    ListNode* tmp = head->next;
    head->next = dummy.next;
    dummy.next = head;
    head = tmp;
  }    
  return dummy.next;
}

{% endhighlight %}
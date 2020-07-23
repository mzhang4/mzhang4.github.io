---
layout: post
title: "19.Remove Nth Node From End of List"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

两个指针，第一个指针先走N步，当第一个指针走到结尾时，则第二个指针指向第倒数N个

{% highlight cpp %}

ListNode* removeNthFromEnd(ListNode* head, int n) {
  ListNode dummy(-1);
  dummy.next = head;
  ListNode* slow = &dummy, *fast = &dummy;

  for (int i = 0; i < n; i++) fast = fast->next;
  while (fast->next) fast = fast->next, slow = slow->next;
  ListNode* tmp = slow->next;
  slow->next = slow->next->next;
  delete tmp;
  return dummy.next;
}

{% endhighlight %}
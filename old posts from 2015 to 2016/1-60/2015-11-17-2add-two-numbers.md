---
layout: post
title: "2.Add Two Numbers"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

由于数本身就是reverse的，所以从list头加到list尾，并且用一个flag记录进位的值

{% highlight cpp %}
ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
  ListNode dummy(-1);
  int carry = 0;

  ListNode* cur = &dummy;

  while (l1 || l2 || carry) {
    if (l1) carry += l1->val, l1 = l1->next;
    if (l2) carry += l2->val, l2 = l2->next;
    cur->next = new ListNode(carry%10);
    cur = cur->next;
    carry /= 10;
  }

  return dummy.next;
}
{% endhighlight %}
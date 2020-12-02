---
layout: post
title: "21.Merge Two Sorted Lists"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

标准的mergesort

{% highlight cpp %}

ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
  ListNode dummy(-1);
  ListNode* cur = &dummy;
  
  while (l1 || l2) {
    if (!l1 || (l2 && l1->val > l2->val)) {
      cur->next = l2;
      l2 = l2->next;
    }
    else {
      cur->next = l1;
      l1 = l1->next;
    }

    cur = cur->next;
  }

  return dummy.next;    
}

{% endhighlight %}
---
layout: post
title: "86. Partition List"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

维护两个列表，一个为小于的，另一个为大于等于的

{% highlight cpp %}

class Solution {
public:
  ListNode* partition(ListNode* head, int x) {
    ListNode dummy1(-1), dummy2(-1);
    ListNode* cur1 = &dummy1, * cur2 = &dummy2;

    while (head) {
      if (head->val < x) {
        cur1->next = head;
        cur1 = cur1->next;
      } else {
        cur2->next = head;
        cur2 = cur2->next;
      }
      head = head->next;
    }

    cur1->next = dummy2.next;
    cur2->next = nullptr;
    
    return dummy1.next;
  }
};

{% endhighlight %}

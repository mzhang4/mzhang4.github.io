---
layout: post
title: "147. Insertion Sort List"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

insertion sort

{% highlight cpp %}

class Solution {
public:
  ListNode* insertionSortList(ListNode* head) {
    ListNode dummy(-1);
    while (head) {
      ListNode* next = head->next;
      ListNode* cur = &dummy;
      
      while (cur->next && cur->next->val <= head->val) {
        cur = cur->next;
      }
      
      head->next = cur->next;
      cur->next = head;
      head = next;
    }
    
    return dummy.next;
  }
};

{% endhighlight %}
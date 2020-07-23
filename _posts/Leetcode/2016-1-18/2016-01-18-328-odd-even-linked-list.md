---
layout: post
title: "328. Odd Even Linked List"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

头插法，将所有的基数点插入头部应该的位置即可

{% highlight cpp %}

class Solution {
public:
  ListNode* oddEvenList(ListNode* head) {
    if (!head || !head->next) return head;
    ListNode* odd = head;
    ListNode* even = head->next;
    ListNode* cur = head;
    
    while (cur && cur->next && cur->next->next) {
      cur = cur->next->next;
      even->next = cur->next;
      cur->next = odd->next;
      odd->next = cur;
      cur = even;
      even = even->next;
      odd = odd->next;
    }
    
    return head;
  }
};

{% endhighlight %}
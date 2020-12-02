---
layout: post
title: "142. Linked List Cycle II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

和第一条是一样的，先判断环是否存在，并且纪录下来相遇的位置，则让fast重新开始，并且每次走一步
当两者再次相遇的时候则就是环的起点

{% highlight cpp %}

class Solution {
public:
  ListNode *detectCycle(ListNode *head) {
    if (!head) return nullptr;
    
    ListNode *fast = head, *slow = head;
    
    while (fast->next && fast->next->next) {
      fast = fast->next->next;
      slow = slow->next;
      if (slow == fast) break;
    }
    
    if (!fast->next || !fast->next->next) return nullptr;
    
    fast = head;
    while (slow != fast) {
      slow = slow->next;
      fast = fast->next;
    }
    
    return slow;
  }
};

{% endhighlight %}

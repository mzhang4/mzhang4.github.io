---
layout: post
title: "141. Linked List Cycle"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

use a slow and fast pointer, if slow == faster then there is a cycle, else if fast meets end, no cycle

{% highlight cpp %}

class Solution {
public:
  bool hasCycle(ListNode *head) {
    ListNode* fast = head, *slow = head;
    while (fast && fast->next) {
      fast = fast->next->next;
      slow = slow->next;
      if (slow == fast)
        return true;
    }    
    return false;
  }
};

{% endhighlight %}

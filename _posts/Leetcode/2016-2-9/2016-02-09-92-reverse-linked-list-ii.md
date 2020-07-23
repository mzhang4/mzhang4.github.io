---
layout: post
title: "92. Reverse Linked List II"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

找到第m个，然后从m＋1个 开始reverse，头插法查到m的前一个，同时更新
m的前一个和m的下一个。

{% highlight cpp %}

class Solution {
public:
  ListNode* reverseBetween(ListNode* head, int m, int n) {
    ListNode dummy(-1);
    dummy.next = head;
    ListNode* prev = &dummy, * cur = head;

    for (int i = 0; i < m-1; i++) {
      prev = prev->next;
      cur = cur->next;
    }

    for (int i = m; i < n; i++) {
      ListNode* tmp = cur->next->next;
      cur->next->next = prev->next;
      prev->next = cur->next;
      cur->next = tmp;
    }

    return dummy.next;
  }
};

{% endhighlight %}

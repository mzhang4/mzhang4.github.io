---
layout: post
title: "160. Intersection of Two Linked Lists"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

go through the A and B, if curA goes to end, then curA point to B,
if curB goes to end then curB point to A. Terminates until curA == curB
Be careful about the details

{% highlight cpp %}

class Solution {
public:
  ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
    ListNode *curA = headA, *curB = headB;
    while (true) {
      if (curA == curB) return curA;
      if (!curA) curA = headB;
      else curA = curA->next;
      if (!curB) curB = headA;
      else curB = curB->next;
    }
  }
};

{% endhighlight %}
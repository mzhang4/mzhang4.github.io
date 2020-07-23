---
layout: post
title: "24.Swap Nodes in Pairs"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

用递归解，swap前两个node，第二个node的next为swapPairs(newhead)

{% highlight cpp %}

ListNode* swapPairs(ListNode* head) {
  if (!head || !head->next) return head;
  ListNode* newHead = head->next->next;
  ListNode* ans = head->next;
  head->next = swapPairs(newHead);
  ans->next = head;
  return ans;
}

{% endhighlight %}

迭代版

{% highlight cpp %}

ListNode* swapPairs(ListNode* head) {
  ListNode* dummy(-1);
  for (ListNode* prev = &dummy, *cur = prev->next, *next = cur ? cur->next : nullptr;
       next;
       prev = cur, cur = prev->next, next = cur ? cur->next : nullptr) {
       prev->next = next;
       cur->next = next->next;
       next->next = cur;
  }
  return dummy.next;
}

{% endhighlight %}
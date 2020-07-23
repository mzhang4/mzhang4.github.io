---
layout: post
title: "25.Reverse Nodes in k Group"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

和上一条一样，可以用递归的方法去做 取出前k个node，进行reverse，head->next = reverseKGroup(newHead, k)
reverse list可以用头插法

{% highlight cpp %}

ListNode* reverseKGroup(ListNode* head, int k) {
  ListNode* cur = head;
  for (int i = 0; i < k-1 && cur; i++) {
    cur = cur->next;
  }

  if (!cur) return head;

  ListNode* newHead = reverseKGroup(cur->next, k);
  cur->next = nullptr;
  cur = reverse(head);  
  head->next = newHead;
  return cur;
}

ListNode* reverse(ListNode* head) {
  ListNode dummy(-1);
  ListNode* cur = head;
  while (cur) {
    ListNode* tmp = cur->next;
    cur->next = dummy.next;
    dummy.next = cur;
    cur = tmp;
  }
  return dummy.next;
}

{% endhighlight %}


combine second step with first one instead of giving cur->next to nullptr

{% highlight cpp %}

ListNode* reverseKGroup(ListNode* head, int k) {
  ListNode* cur = head;
  for (int i = 0; i < k-1 && cur; i++) {
    cur = cur->next;
  }

  if (!cur) return head;

  ListNode* tmp = cur->next;
  ListNode* newHead = reverseKGroup(tmp, k);
  ListNode* prev = nullptr;
  cur = head;
  while (cur != tmp) {
    ListNode* next = cur->next;
    cur->next = prev ? prev : newHead;
    prev = cur;
    cur = next;
  }
  return prev;
}

{% endhighlight %}
---
layout: post
title: "234. Palindrome Linked List"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

找到中间节点，reverse后半部分，进行比较

{% highlight cpp %}

class Solution {
public:
  bool isPalindrome(ListNode* head) {
    if (!head) return true;

    ListNode* slow = head, *fast = head;
    while (fast->next && fast->next->next) {
      fast = fast->next->next;
      slow = slow->next;
    }

    fast = slow->next;
    slow->next = nullptr;
    fast = reverse(fast);

    slow = head;
    while (slow && fast) {
      if (slow->val != fast->val)
        return false;
      fast = fast->next;
      slow = slow->next;
    }

    return true;
  }

  ListNode* reverse(ListNode* root) {
    ListNode dummy(-1);
    ListNode* cur = &dummy;
    while (root) {
      ListNode* tmp = root->next;
      root->next = dummy.next;
      dummy.next = root;
      root = tmp;
    }

    return dummy.next;
    }
};

{% endhighlight %}
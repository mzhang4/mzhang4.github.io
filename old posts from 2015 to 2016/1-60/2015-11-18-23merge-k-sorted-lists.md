---
layout: post
title: "23.Merge k Sorted Lists"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

mergesort的变形，可以用priority_queue 取得当前所有list的最小值，定一个cmp即可
ps: priority_quque, pop出较大的数
ps2: priority_queue的cmp作为第三个参数pass的是template class

{% highlight cpp %}

bool cmp(ListNode* l1, ListNode* l2) {
  if (l1->val != l2->val)
    return l1->val > l2->val;
  return true;
}

ListNode* mergeKLists(vector<ListNode*>& lists) {
  priority_queue <ListNode*, vector <ListNode*>, function<bool(ListNode*, ListNode*)>> pq(cmp);
  for (int i = 0; i < lists.size(); i++) pq.push(lists[i]);
  ListNode dummy(-1);
  ListNode *cur = &dummy;
  while (!pq.empty()) {
    ListNode* tmp = pq.top(); pq.pop();
    cur->next = tmp;
    if (tmp->next) pq.push(tmp->next);
    cur = cur->next;
  }    
  return dummy.next;
}

{% endhighlight %}

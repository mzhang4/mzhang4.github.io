---
layout: post
title: "232. Implement Queue using Stacks"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

one stack used to push, one stack used to pop

{% highlight cpp %}

class Queue {
public:
  // Push element x to the back of queue.
  void push(int x) {
    A.push(x);
  }

  // Removes the element from in front of queue.
  void pop(void) {
    if (B.empty()) {
      while (!A.empty()) {
        B.push(A.top());
        A.pop();
      }
    }
    
    B.pop();
  }

  // Get the front element.
  int peek(void) {
    if (B.empty()) {
      while (!A.empty()) {
        B.push(A.top());
        A.pop();
      }
    }

    return B.top();  
  }

  // Return whether the queue is empty.
  bool empty(void) {
    return A.empty() && B.empty();    
  }
  
  stack <int> A, B;
};

{% endhighlight %}
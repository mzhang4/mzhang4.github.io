---
layout: post
title: "225. Implement Stack using Queues"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}


{% highlight cpp %}

class Stack {
public:
  // Push element x onto stack.
  void push(int x) {
    b.push(x);
    while (!a.empty()) {
      b.push(a.front());
      a.pop();
    }
    swap(a, b);
  }

  // Removes the element on top of the stack.
  void pop() {
    a.pop();
  }

  // Get the top element.
  int top() {
    return a.front();
  }

  // Return whether the stack is empty.
  bool empty() {
    return a.empty();
  }
  
  queue <int> a, b;
};

{% endhighlight %}
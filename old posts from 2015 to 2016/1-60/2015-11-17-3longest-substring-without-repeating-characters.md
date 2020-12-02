---
layout: post
title: "3.Longest Substring Without Repeating Characters"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

1. 用hashmap存储s[i]上一次出现的位置，
2. 用start表示起始位置。
对s进行遍历，对于s[i], 如果他已经在hashmap中，并且他上一次出现的ind不小于start，则更新start ＝ hashmap[s[i]] + 1, 并且更新结果。

ps: 注意，由于start到s的末尾没有算我们还需要再进行一次计算，并且最后计算时，length() 返回的是uninsged int。（max或min需要两者的类型一样，不然会报错）

{% highlight cpp %}

int lengthOfLongestSubstring(string s) {
  int start = 0;
  map <char, int> last;
  int ans = 0;

  for (int i = 0; i < s.length(); i++) {
    if (last.count(s[i]) && last[s[i]] >= start) {
      ans = max(ans, i - 1 - start + 1);
      start = last[s[i]] + 1;
    }

    last[s[i]] = i;
  }

  return max(ans, int(s.length()) - start);
}

{% endhighlight %}
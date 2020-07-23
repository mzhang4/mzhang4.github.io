---
layout: post
title: "12.Integer to Roman"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

和N进制之间的转换累死，不过底数是变化的。
ps: 对于ROMAN数字，当用两个字母进行组合变成新底数时，后一个数不能超过前一个数的10倍

{% highlight cpp %}

string ROMAN[] = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
int VAL[] = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1}; 

string intToRoman(int num) {
  string ans;
  int ind = 0;
  while (num) {
    int t = num/VAL[ind];
    for (int i = 0; i < t; i++) ans += ROMAN[ind];
    num %= VAL[ind++];
  }
  return ans;
}

{% endhighlight %}
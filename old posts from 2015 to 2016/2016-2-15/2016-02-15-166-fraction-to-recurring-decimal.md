---
layout: post
title: "166. Fraction to Recurring Decimal"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

set的考察

{% highlight cpp %}

class Solution {
public:
  string fractionToDecimal(int num, int den) {
    long long numerator = num;
    long long denominator = den;
    int sign = num >= 0 && den >= 0 || num <= 0 && den <= 0 ?  1 : -1;
    numerator = abs(numerator);
    denominator = abs(denominator);
    
    string ans = to_string(numerator/denominator) + '.';
    numerator %= denominator;
    map <int, int> s;

    while (numerator && s.find(numerator) == s.end()) {
      s[numerator] = ans.length();
      numerator *= 10;
      ans += to_string(numerator/denominator);
      numerator %= denominator;
    }

    if (s.find(numerator) != s.end()) {
      int ind = s[numerator];
      ans = ans.substr(0, ind) + "(" + ans.substr(ind) + ")";
    }

    if (ans.back() == '.') ans = ans.substr(0, ans.length() - 1);

    if (sign == -1) ans = "-" + ans;
    
    return ans;
  }
};

{% endhighlight %}
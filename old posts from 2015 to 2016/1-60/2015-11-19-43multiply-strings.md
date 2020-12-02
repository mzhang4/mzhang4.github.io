---
layout: post
title: "43.Multiply Strings"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

细节实现题，按照乘法运算进行计算即可。

{% highlight cpp %}

string multiply(string num1, string num2) {
  int m = num1.size();
  int n = num2.size();
  string ans(m+n+1, '0');
  reverse(num1.begin(), num1.end());

  // num1 * num2[i];

  for (int i = n-1; i>=0; i--) {
    string tmp(m+n+1, '0');
    int carry = 0;
    int n2 = num2[i]-'0';
    int j = 0;
    while (j < m || carry) {
      if (j < m) carry += n2*(num1[j]-'0');
      tmp[n-i-1+j] += carry % 10;
      carry /= 10;
      j++;
    }
    ans = add(ans, tmp);
  }

  int len = ans.size();
  while (len > 1 && ans[len-1] == '0') len--;
    ans = ans.substr(0, len);
    reverse(ans.begin(), ans.end());
    return ans;
}

string add(string a, string b) {
  string ans(a.length(), '0');
  int carry = 0;
  for (int i = 0; i < a.length(); i++) {
    carry += a[i] - '0' + b[i] - '0';
    ans[i] += carry % 10;
    carry /= 10;
  }
  return ans;
}

{% endhighlight %}
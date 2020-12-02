---
layout: post
title: "6.ZigZag Conversion"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

生成zigzag写下之后的n个string，最后将它们连起来
对于s[i]，算出相对位置，加入到相应的string中
Time: O(n), Space O(n)

{% highlight cpp %}

string convert(string s, int numRows) {
  if (numRows == 1) return s;

  vector <string> zigzag(numRows);

  for (int i = 0; i < s.length(); i++) {
    int k = i % (2 * numRows - 2);
    if (k < numRows) zigzag[k] += s[i];
    else zigzag[numRows-(k-numRows)-2] += s[i];
  }

  return accumulate(zigzag.begin(), zigzag.end(), string(""));
}

{% endhighlight %}

或者进行反向思考，得出每一行每一个char对应于原来string的位置
Time: O(n), Space: O(1)

{% highlight cpp %}
string convert(string s, int numRows) {
  if (numRows == 1) return s;
  string ans;
  for (int i = 0; i < numRows; i++) {
    for (int j = 0, index = i; index < s.length(); j++, index += 2 * numRows - 2) {
      ans += s[index];
      if (i == 0 || i == numRows - 1) continue;
      if (index + (numRows - i - 1) * 2 < s.length())
        ans += s[index + (numRows - i -1) * 2];
    }
  }
  return ans;
}

{% endhighlight %}
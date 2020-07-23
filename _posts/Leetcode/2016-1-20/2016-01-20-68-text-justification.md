---
layout: post
title: "68. Text Justification"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

implementation problem
go through each word, if the length of current line exceeds maxWidth then create a new line and add it to ret.

{% highlight cpp %}

class Solution {
public:
  vector<string> fullJustify(vector<string>& words, int maxWidth) {
    vector <string> ret;
    int start = -1;
    int len = 0;

    for (int i = 0; i < words.size(); i++) {
      if (start == -1) start = i;
      len += words[i].length();
      if (i != start) len++;
      if (len > maxWidth) {
        // create a new new line to ret from start to i-1
        ret.push_back(add(start, i-1, words, maxWidth-(len-1-words[i].length())));
        start = i;
        len = words[i].length();
      }
    }

    // add the last line
    string last;
    for (int i = start; i < words.size(); i++) {
      last += words[i];
      if (i != words.size() - 1) last += ' ';
    }
    last += string(int(maxWidth - last.length()), ' ');   
    ret.push_back(last);

    return ret;
  }

  string add(int from, int to, vector <string>& words, int len) {
    string ans;
    if (from == to) return words[from]+string(len, ' ');
    
    len += to-from;
    int t = len/(to-from);
    int k1 = len%(to-from), k2 = (len-k1*(t+1))/t;

    for (int i = from; i < to; i++) {
      ans += words[i];
      if (i-from<k1) {
        ans += string(t+1, ' ');
      } else {
        ans += string(t, ' ');
      }
    }

    ans += words[to];
    return ans;
  }
};

{% endhighlight %}
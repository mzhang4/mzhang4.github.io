---
layout: post
title: "30.Substring with Concatenation of All Words"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

注意，所有单词的长度是一样的, brute force
Time: O(n * sizeof(words))

{% highlight cpp %}

vector<int> findSubstring(string s, vector<string>& words) {
  int len = words[0].length() * words.size();
  vector <int> ans;
  for (int i = 0; i + len <= s.length(); i++) {
    if (ok(s.substr(i, len), words)) {
      ans.push_back(i);
    }
  }
  return ans;
}

bool ok(string s, const vector <string>& words) {
  unordered_map <string, int> wordsMap;
  for (auto w : words) wordsMap[w]++;
  int len = words[0].length();
  for (int i = 0; i + len <= s.length(); i += len) {
    string tmp = s.substr(i, len);
    wordsMap[tmp]--;
    if (wordsMap[tmp] < 0) return false;
  }
  return true;
}

{% endhighlight %}

sliding window, 因为每一个符合条件的字符串，可以对应到0-words[0].length()上，
所以最开始的起始位置算0-words[0].length();
对于下面的每一个word，如果在dict里面，则对应的计数＋1，否则start的位置为j+l
当当前的计数为n时，则找到了所有的单词。push(start)进结果。
这里要注意的是，对于当前word, tmpDict[word] 要小于 dict[word], 如果大于，则将start右移，
并减去右移之后数的count

{% highlight cpp %}

vector<int> findSubstring(string s, vector<string>& words) {
  if (words.size() == 0) return vector <int>();
    
  unordered_map <string, int> dict;
  for (auto w : words) dict[w]++;
  int n = words.size();
  int l = words[0].length();
  vector <int> ans;
    
  for (int i = 0; i < l; i++) {
    int start = i;
    int count = 0;
    unordered_map <string ,int> tmpDict;
    for (int j = i; j < s.length() - l + 1; j += l) {
      string tmp = s.substr(j, l);
      if (dict.count(tmp)) {
        tmpDict[tmp]++;
        count++;
                
        while (tmpDict[tmp] > dict[tmp]) {
          tmpDict[s.substr(start, l)]--;
          start += l;
          count--;
        }
                
        if (count == n) {
          ans.push_back(start);
        }
      }
      else {
        start = j + l;
        count = 0;
        tmpDict.erase(tmpDict.begin(), tmpDict.end());
      }
    }   
  }
    
  return ans;
}

{% endhighlight %}
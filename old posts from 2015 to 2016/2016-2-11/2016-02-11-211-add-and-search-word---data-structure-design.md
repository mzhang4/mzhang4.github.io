---
layout: post
title: "211. Add and Search Word   Data structure design"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

Trie

{% highlight cpp %}

class TrieNode {
public:
  bool isKey;
  TrieNode* next[26];
  TrieNode() {
    isKey = false;
    for (int i = 0; i < 26; i++)
      next[i] = nullptr;
  }
};

class WordDictionary {
public:

  WordDictionary() {
    root = new TrieNode();    
  }
  
  // Adds a word into the data structure.
  void addWord(string word) {
    TrieNode* tmp = root;
    for (int i = 0; i < word.length(); i++) {
      if (!tmp->next[word[i]-'a']) {
        tmp->next[word[i]-'a'] = new TrieNode();
      }
      tmp = tmp->next[word[i]-'a'];
    }
    tmp->isKey = true;
  }

  // Returns if the word is in the data structure. A word could
  // contain the dot character '.' to represent any one letter.
  bool search(string word) {
    return search(root, 0, word);
  }
  
  bool search(TrieNode* cur, int step, string word) {
    if (step == word.length()) {
      return cur->isKey;
    }

    if (word[step] != '.') {
      if (cur->next[word[step]-'a']) return search(cur->next[word[step]-'a'], step+1, word);
      else return false;
    } else {
      for (int i = 0; i < 26; i++) {
        if (cur->next[i] && search(cur->next[i], step + 1, word))
          return true;
      }
    }
    return false;
  }
  
  TrieNode* root;
};

{% endhighlight %}
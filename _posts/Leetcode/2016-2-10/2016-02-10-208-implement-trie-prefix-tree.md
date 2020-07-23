---
layout: post
title: "208. Implement Trie (Prefix Tree)"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

{% highlight cpp %}

class TrieNode {
public:
  // Initialize your data structure here.
  TrieNode() {
    key = false;
    for (int i = 0; i < 26; i++)
      next[i] = nullptr;
  }
  
  bool key;
  TrieNode* next[26];
};

class Trie {
public:
  Trie() {
    root = new TrieNode();
  }

  // Inserts a word into the trie.
  void insert(string word) {
    TrieNode* cur = root;
    for (int i = 0; i < word.length(); i++) {
        if (!cur->next[word[i]-'a']) {
          cur->next[word[i] - 'a'] = new TrieNode(); 
        }
        cur = cur->next[word[i]-'a'];
    }
      
    cur->key = true;
  }

  // Returns if the word is in the trie.
  bool search(string word) {
    TrieNode* cur = root;
    for (int i = 0; i < word.length(); i++) {
      if (!cur->next[word[i]-'a']) {
        return false;
      }
      cur = cur->next[word[i]-'a'];
    }
    
    return cur->key;
  }

  // Returns if there is any word in the trie
  // that starts with the given prefix.
  bool startsWith(string word) {
    TrieNode* cur = root;
    for (int i = 0; i < word.length(); i++) {
      if (!cur->next[word[i]-'a']) {
        return false;
      }
      cur = cur->next[word[i]-'a'];
    }
    
    return true;
  }

private:
  TrieNode* root;
};

{% endhighlight %}
---
layout: post
title: "biweekly contest 40"
description: ""
category: leetcode-contest
tags: leetcode-contest
---
{% include JB/setup %}

After more than 4 years working in Google. I made up my mind that I need to take one more step and trying to find some new journeys.

From today on, I will try to solve leetcode problems and get myself recapped for the algorithm.

1. Maximum Repeating Substring
Check whether n * word is in the sequence or not. Here, I need to remember the API.
string.find(substr) != string::npos.

2. Merge In Between Linked Lists
Find the corresponding positions in the linked list, then modify the linkedlist.

3. Design Front Middle Back Queue
basic operations of vectors. For vectors in c++,  there is no push_front & pop_front. We should use insert(vec.begin() + pos, val) and erase(vec.begin() + pos).
Here there is a small trick here, in order to always access the smaller mid, we can get it by (a.size() - 1) >> 1. (Also, I should remeber the bit operator.)

4. Minimum Number of Removals to Make Mountain Array
For several days, I have strugged in solving leetcode hard problems. This one should be one of the easy ones in hard level. We can rephrase the problem by finding the longest mountain sequence in the array, then we should get the minimum number of steps we need to get for a mountain array.
---
layout: post
title: "4.Median of Two Sorted Arrays"
description: ""
category: leetcode
tags: leetcode
---
{% include JB/setup %}

A[0...n-1]
中位数：当n为奇数时，返回A[n/2], 当n为偶数时，返回(A[n/2] + A[n/2 + 1])/2;
1. 对于本题，最简单的方法是对nums1，nums2进行merge，merge到第n个数即可
Time: O(m+n), Space: O(1)
2. 可以进行优化，取出nums1的中间的数和nums2的中间的数，如果相等，则中位数为此数
如果nums1 > nums2，则nums2前面的所有数可以去掉，递归进行查找
反之如果nums1 < nums2, 同理


Merge
{% highlight cpp %}
double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
  int n = nums1.size() + nums2.size();
  if (n & 0x1) return findKth(nums1, nums2, n/2);
  else return 0.5 * (findKth(nums1, nums2, n/2) + findKth(nums1, nums2, n/2-1));
}

int findKth(vector <int>& nums1, vector <int>& nums2, int k) {
  int p = 0, q = 0;
  int ans;

  for (int i = 0; i <= k; i++) {
    if (p == nums1.size() || (q != nums2.size() && nums1[p] >= nums2[q]))
      ans = nums2[q++];
    else
      ans = nums1[p++];
  }

  return ans;
}
{% endhighlight %}

Second method
ps1: 当k＝＝0时，则len1或者len2为0，此时如果为0的这个数大，则会陷入无穷循环
ps2: 由于求(k+1)/2默认了len1可能占有的k的比例较小，所以如果出现r1-l1>r2-l2，则用len2访问nums2时可能越界。例如r1-l1=2, r2-l2=1，并且k=2时。

{% highlight cpp %}
double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
  int p = nums1.size(), q = nums2.size();
  int n = p + q;
  if (n & 0x1) return findKth(nums1, 0, p-1, nums2, 0, q-1, n/2);
  else return 0.5 * (findKth(nums1, 0, p-1, nums2, 0, q-1, n/2) + 
                     findKth(nums1, 0, p-1, nums2, 0, q-1, n/2-1));
}

int findKth(vector <int>& nums1, int l1, int r1, 
            vector <int>& nums2, int l2, int r2, int k) {
  if (r1 - l1 > r2 - l2) return findKth(nums2, l2, r2, nums1, l1, r1, k);
  if (l1 > r1) return nums2[l2+k];
  if (l2 > r2) return nums1[l1+k];
  if (k == 0) return min(nums1[l1], nums2[l2]);
  int len1 = min(r1-l1+1, (k+1)/2), len2 = k + 1 - len1;
  if (nums1[l1+len1-1] == nums2[l2+len2-1]) return nums1[l1+len1-1];
  else if (nums1[l1+len1-1] > nums2[l2+len2-1])
    return findKth(nums1, l1, r1, nums2, l2+len2, r2, k - len2);
  else
    return findKth(nums1, l1+len1, r1, nums2, l2, r2, k - len1);
}
{% endhighlight %}

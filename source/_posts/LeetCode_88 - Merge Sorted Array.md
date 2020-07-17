
---
title: LeetCode|Array|88 Merge Sorted Array
date: 2020-07-14 12:12:57
categories: 
- LeetCode
tag: ["LeetCode","Array"]
---
# 题目
[88. Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)
Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

Note:

The number of elements initialized in nums1 and nums2 are m and n respectively.
You may assume that nums1 has enough space (size that is equal to m + n) to hold additional elements from nums2.
Example:

Input:
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

Output: [1,2,2,3,5,6]
 

Constraints:

-10^9 <= nums1[i], nums2[i] <= 10^9
nums1.length == m + n
nums2.length == n
# 解题
## 1

```javascript
/**
 * @param {number[]} nums1
 * @param {number} m
 * @param {number[]} nums2
 * @param {number} n
 * @return {void} Do not return anything, modify nums1 in-place instead.
 */
var merge = function(nums1, m, nums2, n) {
    var len = m + n
    m --;
    n --;
    while(len--){
         if (n < 0 || nums1[m] > nums2[n]) {
            nums1[len] = nums1[m--];
        } else {
            nums1[len] = nums2[n--];
        }
    }
    
};
```
## 2
先复制，然后再排序（默认）

``` javascript
let merge = (A, M, B, N) => {
    for (let i = M; i < M + N; ++i)
        A[i] = B[i - M];
    A.sort((a, b) => a - b);
};
```
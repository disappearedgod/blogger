
---
title: LeetCode|Array|350 Intersection_of_Two_Arrays_II
date: 2020-07-14 12:12:57
categories: 
- LeetCode
tag: ["LeetCode","Array"]
---

# [题目](https://leetcode.com/problems/intersection-of-two-arrays-ii/)

Given two arrays, write a function to compute their intersection.

Example 1:

```
Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2,2]
```

Example 2:

```
Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [4,9]
```

Note:

Each element in the result should appear as many times as it shows in both arrays.
The result can be in any order.
Follow up:

What if the given array is already sorted? How would you optimize your algorithm?
What if nums1's size is small compared to nums2's size? Which algorithm is better?
What if elements of nums2 are stored on disk, and the memory is limited such that you cannot load all elements into the memory at once?

# 解题思路

### 需要内存，不需要排序
#### HASHMAP
```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersect = function(nums1, nums2) {
    let map1 = countNums(nums1);
    let map2 = countNums(nums2);
    let res = [];
    
    for(let num of map1.keys()){
        const count = Math.min(map1.get(num), map2.get(num));
        for(let i = 0; i < count; i++){
            res.push(num);
        }
    }
    return res;
};

function countNums(nums){
    let map = new Map()
    for(let i = 0; i < nums.length; i++){
        let num = nums[i];
        let count = map.get(num);
        
        if(count){
             map.set(num, count + 1);
        }
        else{
            map.set(num, 1);
        }
    }
    return map;
}
```
#### Array

```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersect = function (nums1, nums2) {
    let solution = [];
    if (nums1.length < nums2.length) {
        return intersect(nums2, nums1);
    }
    // Instead of HashMap, nums1 to acculate
    // [1, 2, 2, 1]
    // {'1':2, '2':2}   
    const obj = nums1.reduce((acc, num) => {
        acc[num] = acc[num] + 1 || 1;
        return acc;
    }, {});
  
    //find the num in nums2
    for (let i = 0; i < nums2.length; i++) {
    if (obj[nums2[i]] !== undefined && obj[nums2[i]] > 0) {
      obj[nums2[i]] = obj[nums2[i]] - 1;
      solution.push(nums2[i]);
    }
    }

  return solution;
};
```

### 需要排序
#### 双指针解题
```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersect = function(nums1, nums2) {
    let res = [];
    
    //Sort array
    nums1.sort((a, b) => a - b);
    nums2.sort((a, b) => a - b);
    
    let i = 0;
    let j = 0;
    
    while(i<nums1.length && j< nums2.length){
        let x = nums1[i];
        let y = nums2[j];
        if(x === y){
            res.push(nums1[i]);
            i++;
            j++;
        }
        else if(x > y){
            j++;
        }
        else{
            // x < y;
            i++;
        }
    }
    
    return res;
}
```

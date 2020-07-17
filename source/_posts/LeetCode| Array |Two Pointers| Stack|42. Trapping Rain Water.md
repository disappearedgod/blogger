---
title: LeetCode| Array |Two Pointers| Stack|42. Trapping Rain Water
date: 2020-07-17 13:12:57
categories: 
- LeetCode
type: ["LeetCode","Array","Two Pointers","Stack"]
---

# [Problem ](https://leetcode.com/problems/trapping-rain-water/)

Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it is able to trap after raining.

![](LeetCode_Greedy_455_Assign Cookies.png)

The above elevation map is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped. Thanks Marcos for contributing this image!

Example:

> Input: [0,1,0,2,1,0,1,3,2,1,2,1]
> Output: 6
> 
> 
# Solve
左右 底部 三个点
左边最大 - 底部
右边最大 - 底部 

```javascript
/**
 * @param {number[]} height
 * @return {number}
 */
var trap = function(height) {
    let left = 0, right = height.length -1;
    let leftMax = -1, rightMax = -1;
    let res = 0;
    
    while(left < right){
        leftMax =  height[left] > leftMax ? height[left] : leftMax;
        rightMax =  height[right] > rightMax ? height[right] : rightMax;
        
        if(leftMax > rightMax){
            res += rightMax - height[right];
            right --;
        }
        else{
            res += leftMax - height[left];
            left ++;
        }
    }
    return res;
};
```
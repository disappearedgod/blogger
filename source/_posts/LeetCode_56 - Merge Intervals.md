
---
title: LeetCode|stack|56 Merge Intervals
date: 2020-07-14 12:12:57
categories: 
- LeetCode
tag: ["LeetCode","stack"]
---

# [题目](https://leetcode.com/problems/merge-intervals/)

Given a collection of intervals, merge all overlapping intervals.

Example 1:

> Input: [[1,3],[2,6],[8,10],[15,18]]
> Output: [[1,6],[8,10],[15,18]]
> Explanation: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].

Example 2:

> Input: [[1,4],[4,5]]
> Output: [[1,5]]
> Explanation: Intervals [1,4] and [4,5] are considered overlapping.

NOTE: input types have been changed on April 15, 2019. Please reset to default code definition to get new method signature.

# 解题
##  js默认sort

```javascript
/**
 * @param {number[][]} intervals
 * @return {number[][]}
 */
var merge = function(intervals) {
    if (intervals.length == 0) return [];
    
    intervals.sort((a, b) => b[0] - a[0]);
    
    const res = [intervals.pop()];
    
     while (intervals.length > 0) {
        const [a, b] = res[res.length - 1];
        const [c, d] = intervals.pop();
        
        if(b >= c){
            const start = Math.min(a, c);
            const end = Math.max(b, d);
            
            res[res.length - 1][0] = start;
            res[res.length - 1][1] = end;
        }
        else{
            res.push([c, d])
        }
    }
    
    return res;
};
```


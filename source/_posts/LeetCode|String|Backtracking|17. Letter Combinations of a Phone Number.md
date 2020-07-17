---
title: LeetCode|String|Backtracking|17. Letter Combinations of a Phone Number
date: 2020-07-17 13:12:57
categories: 
- LeetCode
type: ["LeetCode","String","Backtracking"]
---


# [Problem ](https://leetcode.com/problems/trapping-rain-water/)

Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.


const map = {
    2:"abc",
    3:"def",
    4:"ghi",
    5:"jkl",
    6:"mno",
    7:"pqrs",
    8:"tuv",
    9:"wxyz",
}

Example:

Input: "23"
Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].

# Solve

回溯方法：
1. 遍历+ 字符串返回
2. 字符串返回遍历：char遍历 利用map

```javascript
/**
 * @param {string} digits
 * @return {string[]}
 */
var letterCombinations = function(digits) {
    let res = [];
    let len = digits.length;
    if(len === 0)
        return res;
    
    function go(n, str){
        if(n === len){
            res.push(str);
            return;
        }
        
        for(let char of map[digits[n]]){
            go(n + 1 ,str + char);
        }
    }
    
    go(0, '');
    
    return res;
    
};

const map = {
    2:"abc",
    3:"def",
    4:"ghi",
    5:"jkl",
    6:"mno",
    7:"pqrs",
    8:"tuv",
    9:"wxyz",
}
```

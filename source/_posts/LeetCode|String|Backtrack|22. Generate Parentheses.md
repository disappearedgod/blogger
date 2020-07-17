---
title: LeetCode|String|Backtrack|22. Generate Parentheses
date: 2020-07-17 05:12:57
categories: 
- LeetCode
type: ["LeetCode","Backtracking"]
---

# Problem

Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

For example, given n = 3, a solution set is:

```
 [
   "((()))",
   "(()())",
   "(())()",
   "()(())",
   "()()()"
 ]
```


# Solve

```javascript
/**
 * @param {number} n
 * @return {string[]}
 */
var generateParenthesis = function(n) {
    let res = []
    
    function go(left, right, str){
        if(left > right)
            return;
        
        if(left ===0 && right ===0){
            res.push(str);
        }
        
        if(left > 0)
            go(left-1, right, str + '(');
        if(right > 0)
            go(left, right-1, str + ')');
    }
    go(n,n,'')
    
    return res;
};
```
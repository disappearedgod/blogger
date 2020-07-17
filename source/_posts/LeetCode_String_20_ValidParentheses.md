---
title: LeetCode|String|20 ValidParentheses
date: 2020-07-14 12:12:57
categories: 
- LeetCode
type: ["LeetCode","String"]
---
# Problem

Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Note that an empty string is also considered valid.

Example 1:

> Input: "()"
> Output: true

Example 2:

> Input: "()[]{}"
> Output: true

Example 3:

> Input: "(]"
> Output: false

Example 4:

> Input: "([)]"
> Output: false

Example 5:

> Input: "{[]}"
> Output: true

# Solve

### String

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
    let preS = ''
    while(s !== preS){
        preS = s
        s = s.split('()').join('')
        s = s.split('[]').join('')
        s = s.split('{}').join('') 
    }
    if(!s)
        return true;
    return false;
};
```

### Stack

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
    const stack = []
    
    for(let i = 0; i < s.length; i++){
        let c = s.charAt(i);
        switch(c){
            case '(':
                stack.push(')');
                break;
            case '{':
                stack.push('}');
                break;
            case '[':
                stack.push(']');
                break;
            default:
                if(c !== stack.pop()){
                    return false;
                }
        }
    }
    return stack.length === 0
};
```


> Runtime: 88 ms, faster than 21.46% of JavaScript online submissions for Valid Parentheses.
> Memory Usage: 33.1 MB, less than 99.01% of JavaScript online submissions for Valid Parentheses.

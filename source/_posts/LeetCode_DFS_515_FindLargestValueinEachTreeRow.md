---
title: LeetCode|DFS|515 FindLargestValueinEachTreeRow

date: 2020-07-14 12:12:57
categories: 
- LeetCode
tag: ["LeetCode","DFS"]
---

# 题目
ou need to find the largest value in each row of a binary tree.

Example:

> Input: 
> 
>           1
>          / \
>         3   2
>        / \   \  
>       5   3   9 
> 
> Output: [1, 3, 9]

### 解题思路

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[]}
 */
var largestValues = function(root) {
    const res = []
    if(!root){
        return res;
    }
    
    var helper = (node, i) => {
        res[i] = res[i] > node.val ? res[i]  : node.val;

        if(node.left !== null){
            helper(node.left, i + 1)
        }

        if(node.right !== null){
            helper(node.right, i + 1)
        }
    };
    
    helper(root, 0)
    
    return res;
};
```
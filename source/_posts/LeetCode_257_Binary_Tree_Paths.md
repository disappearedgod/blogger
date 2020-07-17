
---
title: LeetCode|DFS|257 Binary_Tree_Paths
date: 2020-07-14 12:12:57
categories: 
- LeetCode
tag: ["LeetCode","DFS"]
---

# Problem
Given a binary tree, return all root-to-leaf paths.

Note: A leaf is a node with no children.

Example:

> Input:
> 
>    1
>  /   \
> 2     3
>  \
>   5
> 
> Output: ["1->2->5", "1->3"]

Explanation: All root-to-leaf paths are: 1->2->5, 1->3

# Sovle


### 递归

用当前节点的值去拼接左右子树递归调用当前函数获得的所有路径。

也就是根节点拼上以左子树为根节点得到的路径，加上根节点拼上以右子树为根节点得到的所有路径。

直到叶子节点，仅仅返回包含当前节点的值的数组。


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
 * @return {string[]}
 */
var binaryTreePaths = function(root) {
    let res = [];
    traverse(root, "");
    
    function traverse(node ,path){
        if(!node)
            return;
        
        if(!node.left && !node.right){
            res.push(path + node.val)
            return;
        }
        
        traverse(node.left, path + node.val + "->" );
        traverse(node.right, path + node.val + "->" );
        
    }
    
    return res;
};
```
### 迭代

```javascript
var binaryTreePaths = function(root) {
    let paths = []
    
    if(!root)
        return paths;
    
    let queue = [[root, []]];
    
    while(queue.length){
        const [node, res] = queue.shift();
        
        if(!node.left && !node.right){
        	// array to string
            paths.push(res.concat([node.val]).join('->'));
            continue;
        }
        
        if(node.left !== null){
            queue.push([node.left ,res.concat([node.val])]);
        }
        
        if(node.right !== null){
            queue.push([node.right ,res.concat([node.val])]);
        }
    }
    
    
    return paths
};
```
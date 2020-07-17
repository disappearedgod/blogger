---
title: LeetCode|Tree| 617 Merge_Tree
date: 2020-07-14 12:12:57
categories: 
- LeetCode
type: ["LeetCode","Tree"]
---

# [题目](https://leetcode.com/problems/merge-two-binary-trees/)

617- Merge Two Binary Trees

Given two binary trees and imagine that when you put one of them to cover the other, some nodes of the two trees are overlapped while the others are not.

You need to merge them into a new binary tree. The merge rule is that if two nodes overlap, then sum node values up as the new value of the merged node. Otherwise, the NOT null node will be used as the node of new tree.

Example 1:

> Input: 
> 	Tree 1                     Tree 2                  
>           1                         2                             
>          / \                       / \                            
>         3   2                     1   3                        
>        /                           \   \                      
>       5                             4   7                  
> Output: 
> Merged tree:
> 	     3
> 	    / \
> 	   4   5
> 	  / \   \ 
> 	 5   4   7
 

Note: The merging process must start from the root nodes of both trees.

# JS
## 递归
``` javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} t1
 * @param {TreeNode} t2
 * @return {TreeNode}
 */
 //递归算法：
//
// 1.以预购方式遍历树
// 2.检查两个树节点是否均为NULL
// 1.如果不是，则更新值
// 3.递归左子树
// 4.重复右子树
// 5.返回更新的树的根
var mergeTrees = function(t1, t2) {
    if(!t1 && !t2){
        return null;
    }
    if(!t1 || !t2){
        return t1 || t2;
    }
    
    var root = new TreeNode(t1.val + t2.val);
    
    root.left = mergeTrees(t1.left, t2.left);
    root.right = mergeTrees(t1.right, t2.right);
    
    return root;
    
};
```

## 非递归(迭代）
```
//迭代算法：
//
// 1.创建一个堆栈
// 2.将两棵树的根节点推入堆栈。
// 3.当堆栈不为空时，执行以下步骤：
	// 1.从堆栈顶部弹出一个节点对
	// 2.对于每个删除的节点对，添加与两个节点对应的值，并更新第一棵树中相应节点的值
	// 3.如果第一棵树的左子节点存在，则将两棵树的左子节点（对）推入堆栈。
	// 4.如果第一棵树的左子节点不存在，则将第二棵树的左子节点附加到第一棵树的当前节点
	// 5.对正确的子对也执行相同的操作。
	// 6.如果当前两个节点均为NULL，则继续从堆栈中弹出下一个节点。
//4. 返回
```
迭代算法

```javascript
const mergeTrees = (t1, t2) => {
  if (t1 === null) {
    return t2;
  }
  const stack = [];
  stack.push([t1, t2]);
  while (stack.length !== 0) {
    const t = stack.pop();
    if (t[0] === null || t[1] === null) {
      continue;
    }
    t[0].val += t[1].val;
    if (t[0].left === null) {
      t[0].left = t[1].left;
    } else {
      stack.push([t[0].left, t[1].left]);
    }
    if (t[0].right === null) {
      t[0].right = t[1].right;
    } else {
      stack.push([t[0].right, t[1].right]);
    }
  }
  return t1;
};
```

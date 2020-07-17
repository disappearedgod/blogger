
---
title: LeetCode|24 Swap Node In Pairs
date: 2020-07-14 12:12:57
categories: 
- LeetCode
tag: ["LeetCode","TwoPointer"]
---
# Problem
Given a linked list, swap every two adjacent nodes and return its head.

You may not modify the values in the list's nodes, only nodes itself may be changed.

 

Example:

> Given 1->2->3->4, you should return the list as 2->1->4->3.

# Sovle
### Link Table
这题本意比较简单，1 -> 2 -> 3 -> 4 的情况下可以定义一个递归的辅助函数 helper，这个辅助函数对于节点和它的下一个节点进行交换，比如 helper(1) 处理 1 -> 2，并且把交换变成 2 -> 1 的尾节点 1的next继续指向 helper(3)也就是交换后的 4 -> 3。

边界情况在于，如果顺利的作了两两交换，那么交换后我们的函数返回出去的是 交换后的头部节点，但是如果是奇数剩余项的情况下，没办法做交换，那就需要直接返回 原本的头部节点。这个在 helper函数和主函数中都有体现。

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var swapPairs = function(head) {
    if(!head){
        return null;
    }
    
    let helper = function (node) {
        let tempNext = node.next;
        if(tempNext){
            let tempNextNext = node.next.next; //1 --> 3-->
            //swap 1-> 2 to 2->1
            node.next.next = node;
            //2 -> 1 --->
            node.next = tempNextNext ? helper(tempNextNext) : null;
            
            return tempNext || node;
        }
    };
    
    let res =helper(head);
    
    return res || head;
};

```

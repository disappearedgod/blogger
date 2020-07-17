---
title: LeetCode|String|Backtrack|2. Add Two Numbers
date: 2020-07-17 05:12:57
categories: 
- LeetCode
type: ["LeetCode","Backtracking"]
---

# [Problem](https://leetcode.com/problems/add-two-numbers/)
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Example:

> Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
> Output: 7 -> 0 -> 8
> Explanation: 342 + 465 = 807.


# Solve

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var addTwoNumbers = function(l1, l2) {
  const head = new ListNode();
  let cursor = head;
  let carry = 0;
  while (l1 || l2 || carry) {
    cursor.next = new ListNode();
    cursor = cursor.next;
    let val = (l1 ? l1.val : 0) + (l2 ? l2.val : 0) + carry;
    carry = val >= 10 ? 1 : 0;
    cursor.val = val % 10;
    l1 = l1 ? l1.next : null;
    l2 = l2 ? l2.next : null;
  }
  return head.next;
};
```

### self

```javascript
var addTwoNumbers = function(l1, l2) {
    let res = new ListNode(-1), dummy = res, sum = 0,carry = 0;
    
    if(!l1 || !l2){
        return l1  || l2;
    }
    
    while(l1 || l2 || sum> 0){
        if(l1){
            sum += l1.val;
            l1 = l1.next;
        }
        
        if(l2){
            sum += l2.val;
            l2 = l2.next;
        }
        
        if(sum >= 10){
            sum -= 10;
            carry = 1;
        }
        
        dummy.next = new ListNode(sum);
        dummy = dummy.next;
        sum = carry;
        carry = 0;
    }
    
    return res.next;
};

```

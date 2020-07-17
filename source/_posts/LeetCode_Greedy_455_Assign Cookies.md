---
title: LeetCode|Greedy|455 Assign Cookies
date: 2020-07-14 12:12:57
categories: 
- LeetCode
type: ["LeetCode","Greedy"]
---


# Problem 

Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie. Each child i has a greed factor gi, which is the minimum size of a cookie that the child will be content with; and each cookie j has a size sj. If sj >= gi, we can assign the cookie j to the child i, and the child i will be content. Your goal is to maximize the number of your content children and output the maximum number.

Note:
You may assume the greed factor is always positive. 
You cannot assign more than one cookie to one child.

Example 1:

> Input: [1,2,3], [1,1]
> 
> Output: 1
> 
> Explanation: You have 3 children and 2 cookies. The greed factors of 3 children are 1, 2, 3. 
> And even though you have 2 cookies, since their size is both 1, you could only make the child whose greed factor is 1 content.
> You need to output 1.

Example 2:

> Input: [1,2], [1,2,3]
> 
> Output: 2
> 
> Explanation: You have 2 children and 3 cookies. The greed factors of 2 children are 1, 2. 
> You have 3 cookies and their sizes are big enough to gratify all of the children, 
> You need to output 2.


# Solve

### itr

饼干和孩子的需求都排序好，然后从最小的饼干分配给需求最小的孩子开始，不断的尝试新的饼干和新的孩子，这样能保证每个分给孩子的饼干都恰到好处的不浪费，又满足需求。

利用双指针不断的更新 i 孩子的需求下标和 j饼干的值，直到两者有其一达到了终点位置：

如果当前的饼干不满足孩子的胃口，那么把 j++ 寻找下一个饼干，不用担心这个饼干被浪费，因为这个饼干更不可能满足下一个孩子（胃口更大）。
如果满足，那么 i++; j++; count++ 记录当前的成功数量，继续寻找下一个孩子和下一个饼干。

```javascript
/**
 * @param {number[]} g
 * @param {number[]} s
 * @return {number}
 */
var findContentChildren = function(g, s) {
    g.sort((a,b) => a - b)
    s.sort((a,b) => a - b)
    
    let i = 0;
    let j = 0;
    let count = 0;
    while(i < g.length && j < s.length){
        let need = g[i];
        let cookie = s[j];
        
        if(cookie >= need){
            count ++;
            i++;
            j++;
        }
        else{
            j++;
        }
    }
    
    return count;
};
```

### Resource

[here](https://mp.weixin.qq.com/s/7mJSpnHE319swy0LStpavQ)
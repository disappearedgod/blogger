
---
title: LeetCode|DFS|198 HouseRobber
date: 2020-07-14 12:12:57
categories: 
- LeetCode
tag: ["LeetCode","DFS"]
---


# [Problem ](https://leetcode.com/problems/house-robber/)

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

 

Example 1:

> Input: nums = [1,2,3,1]
> Output: 4
> Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
>              Total amount you can rob = 1 + 3 = 4.

Example 2:

> Input: nums = [2,7,9,3,1]
> Output: 12
> Explanation: Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
>              Total amount you can rob = 2 + 9 + 1 = 12.
> 

# Solve

### DP

动态规划的一个很重要的过程就是找到「状态」和「状态转移方程」，在这个问题里，设 i 是当前屋子的下标，状态就是 以 i 为起点偷窃的最大价值

在某一个房子面前，盗贼只有两种选择：偷或者不偷。

偷的话，价值就是「当前房子的价值」+「下两个房子开始盗窃的最大价值」
不偷的话，价值就是「下一个房子开始盗窃的最大价值」
在这两个值中，选择最大值记录在 dp[i]中，就得到了以 i 为起点所能偷窃的最大价值。。

动态规划的起手式，找基础状态，在这题中，以终点为起点的最大价值一定是最好找的，因为终点不可能再继续往后偷窃了，所以设 n 为房子的总数量， dp[n - 1] 就是 nums[n - 1]，小偷只能选择偷窃这个房子，而不能跳过去选择下一个不存在的房子。


```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var rob = function(nums) {
    if(nums.length === 0){
        return 0;
    }
    let dp = [];
    
    for(let i = nums.length - 1; i >= 0; i--){
        let robNow = nums[i] + (dp [i + 2] || 0);
        let robNext = dp[i + 1] || 0;
        
        dp[i] = Math.max(robNow, robNext);
    }
    
    return dp[0];
};

```


# resource
[here](https://mp.weixin.qq.com/s/7mJSpnHE319swy0LStpavQ)


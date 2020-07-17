---
title: LeetCode|Two_Pointer|16 3Sum Closet
date: 2020-07-14 12:12:57
categories: 
- LeetCode
type: ["LeetCode","Two_Pointer"]
---

# 题目

16—[3Sum Closest](https://leetcode.com/problems/3sum-closest/)
Medium

Given an array nums of n integers and an integer target, find three integers in nums such that the sum is closest to target. Return the sum of the three integers. You may assume that each input would have exactly one solution.

 

Example 1:

```
Input: nums = [-1,2,1,-4], target = 1
Output: 2
Explanation: The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
```
 

Constraints:
```
3 <= nums.length <= 10^3
-10^3 <= nums[i] <= 10^3
-10^4 <= target <= 10^4
```
# 解题

### 双指针
先按照升序排序，然后分别从左往右依次选择一个基础点 i（0 <= i <= nums.length - 3），在基础点的右侧用双指针去不断的找最小的差值。

假设基础点是 i，初始化的时候，双指针分别是：

left：i + 1，基础点右边一位。
right: nums.length - 1 数组最后一位。
然后求此时的和，如果和大于 target，那么可以把右指针左移一位，去试试更小一点的值，反之则把左指针右移。

在这个过程中，不断更新全局的最小差值 min，和此时记录下来的和 res。

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var threeSumClosest = function(nums, target) {
    let len = nums.length;
    if(len === 3){
        return getSum(nums);
    }
    
    nums.sort((a,b)=> a-b);
    
    let min = Infinity;
    let res;
    for(let i = 0; i < len - 2; i++){
        let basic = nums[i];
        let left = i + 1;
        let right = len - 1;
        
        while(left < right){
            let sum = basic + nums[left] + nums[right];
            let diff = Math.abs(sum - target);
            
            if(diff < min){
                min = diff;
                res = sum;
            }
            
            if(sum < target){
                left ++;
            }
            else if( sum > target){
                right --;
            }
            else{
                return sum;
            }
        }
    }
    
    return res;
};

function getSum(nums){
    return nums.reduce((total, cur)=> total + cur, 0)
}
```

### 来源
[双指针问题](https://mp.weixin.qq.com/s/7mJSpnHE319swy0LStpavQ)

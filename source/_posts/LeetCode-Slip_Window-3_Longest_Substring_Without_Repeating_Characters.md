
---
title: LeetCode| Slip_Window| 3_Longest_Substring_Without_Repeating_Characters
date: 2020-07-14 12:12:57
categories: 
- LeetCode
tag: ["LeetCode","Slip_Window"]
---

# 题目
Given a string, find the length of the longest substring without repeating characters.

Example 1:

```
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
```

Example 2:

```
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

Example 3:

```
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

# 解题思路
### HashTable & keeping track
Runs at Time: O(n) and Space: O(min(n + m)) 

这题是比较典型的滑动窗口问题，定义一个左边界 left 和一个右边界 right，形成一个窗口，并且在这个窗口中保证不出现重复的字符串。

这需要用到一个新的变量 freqMap，用来记录窗口中的字母出现的频率数。在此基础上，先尝试取窗口的右边界再右边一个位置的值，也就是 str[right + 1]，然后拿这个值去 freqMap 中查找：

这个值没有出现过，那就直接把 right ++，扩大窗口右边界。
如果这个值出现过，那么把 left ++，缩进左边界，并且记得把 str[left] 位置的值在 freqMap 中减掉。
循环条件是 left < str.length，允许左边界一直滑动到字符串的右界。

```javascript
/**
 * @param {string} s
 * @return {number}
 */
let lengthOfLongestSubstring = function (str) {
  let n = str.length
  // 滑动窗口为s[left...right]
  let left = 0
  let right = -1
  let freqMap = {} // 记录当前子串中下标对应的出现频率
  let max = 0 // 找到的满足条件子串的最长长度

  while (left < n) {
    let nextLetter = str[right + 1]
    if (!freqMap[nextLetter] && nextLetter !== undefined) {
      freqMap[nextLetter] = 1
      right++
    } else {
      freqMap[str[left]] = 0
      left++
    }
    max = Math.max(max, right - left + 1)
  }

  return max
}
```

Hi this is a really elegant solution using hash table and keeping track, when was the last time we saw a certain character. While the characters are not repeating we are updating the longest variable, once we get to repeating we update the start_idx from which we start trimming the original string

Runs at Time: O(n) and Space: O(min(n + m)) where n is the number of characters in a string and m is the number of characters in alphabet of string. If every single character of an alphabet is included, we will end up using them all, and if not then we gonna at most use n characters, so min of those to makes sanse

```javascript
var lengthOfLongestSubstring = function(s) {
    if(!s){
        return 0;
    }
    
    let map = {};
    let start = 0;
    let max = 0;
    
    for(let i = 0; i < s.length; i++){
        const c = s.charAt(i);
        
        if(map[c] !== undefined && map[c] >= start){
            max = Math.max(max, i - start);
            start = map[c] + 1;
        }
        
        map[c] = i;
    }
    
    max = Math.max(max, s.length - start)
    
    return max
};
```


### JS function

```javascript
const lengthOfLongestSubstring = s => {
    // keeps track of the most recent index of each letter.
    const map = {};
    // keeps track of the starting index of the current substring.
    var left = 0;
    
    return s.split('').reduce((max, v, i) => {
        // starting index of substring is 1 + (the last index of this letter) to ensure this letter is not counted twice.
        left = map[v] >= left ? map[v] + 1 : left;
        // updates last recorded index of letter to the most recent index.
        map[v] = i;
        
        // indices of current substring is (idx - leftIdx, idx).
        // +1 because if your substring starts and ends at index 0, it still has a length of 1.
        return Math.max(max, i - left + 1);
    }, 0)
};
```
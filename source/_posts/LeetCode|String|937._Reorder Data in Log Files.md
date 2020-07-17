
---
title: LeetCode|String|937. Reorder Data in Log Files
date: 2020-07-17 02:12:57
categories: 
- LeetCode
type: ["LeetCode","String"]

---

# Problem

You have an array of logs.  Each log is a space delimited string of words.

For each log, the first word in each log is an alphanumeric identifier.  Then, either:

Each word after the identifier will consist only of lowercase letters, or;
Each word after the identifier will consist only of digits.
We will call these two varieties of logs letter-logs and digit-logs.  It is guaranteed that each log has at least one word after its identifier.

Reorder the logs so that all of the letter-logs come before any digit-log.  The letter-logs are ordered lexicographically ignoring identifier, with the identifier used in case of ties.  The digit-logs should be put in their original order.

Return the final order of the logs.

 

> Example 1:
> 
> Input: logs = ["dig1 8 1 5 1","let1 art can","dig2 3 6","let2 own kit dig","let3 art zero"]
> Output: ["let1 art can","let3 art zero","let2 own kit dig","dig1 8 1 5 1","dig2 3 6"]
>  

Constraints:

> 0 <= logs.length <= 100
> 3 <= logs[i].length <= 100
> logs[i] is guaranteed to have an identifier, and a word after the identifier.


# Solve

```javascript
var reorderLogFiles = function(logs) {
  let letters = [];
  let digits = [];
  
  for (let i = 0; i < logs.length; i++) {
    if (isFinite(logs[i].split(' ')[1])) {
      digits.push(logs[i]);
    } else letters.push(logs[i]);
  } 
  
  letters.sort((a,b) => {
    let aCut = a.slice(a.indexOf(' ') + 1);
    let bCut = b.slice(b.indexOf(' ') + 1);
    if (aCut === bCut) {
      return a > b ? 1 : -1;
    } else return aCut > bCut ? 1 : -1; 
  });
  
  return [...letters, ...digits]
};
```


```javascript
var reorderLogFiles = function(logs) {
    // String to array
    const body = s => s.slice(s.indexOf(' ') + 1) ;
    // Boolean 
    const isNum = c => /\d/.test(c);
    
    //compare id
    const compare = (a, b) => {
        const n = body(a).localeCompare(body(b));
        if(n !== 0)
            return n;
        return a.localeCompare(b);
    };
    
    const digitLogs = [];
    const letterLogs = [];
    
    for( const log of logs){
        if (isNum(body(log))) digitLogs.push(log);
        else letterLogs.push(log);
    }
    
    return [...letterLogs.sort(compare), ...digitLogs];
    
};
```
